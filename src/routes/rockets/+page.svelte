<script>
  import { base } from "$app/paths";
  import { Column, Row, Tile } from "carbon-components-svelte";
  import { Rocket } from "carbon-pictograms-svelte";
  import CreateRocket from "../../components/modals/CreateRocket.svelte";
  import { consensusTipState } from "$lib/stores/nostrocket_state/master_state";
</script>

<Row>
  <Column sm={8}>
    <CreateRocket />
  </Column>
</Row>
<Row>
  {#each [...$consensusTipState.RocketMap] as [key, rocket]}
    <Column max={8}>
      <Tile style="margin:1px;">
        <!-- <Avatar ndk={$ndk} pubkey={rocket.CreatedBy} /> -->
        <h3><Rocket />{rocket.Name}</h3>
        <p>
          Problem: {rocket.ProblemID
            ? rocket.ProblemID
            : "No Associated Problem"}
        </p>
        <p>Event ID: {key}</p>
        <p>Created By: {rocket.CreatedBy}</p>
        <a href="{base}/rockets/{key}">More...</a>
      </Tile>
    </Column>
  {/each}
</Row>
