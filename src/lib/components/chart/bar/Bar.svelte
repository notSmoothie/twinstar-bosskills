<script lang="ts">
	import type { LayerCake } from 'layercake';
	import { getContext } from 'svelte';

	const { data, xGet, yGet, xScale, yScale } = getContext<LayerCake>('LayerCake');

	/** @type {String} [fill='#00bbff'] - The shape's fill color. This is technically optional because it comes with a default value but you'll likely want to replace it with your own color. */
	export let fill: string = 'var(--color-primary)';
</script>

<g class="bar-group">
	{#each $data as d, i}
		<rect
			class="group-rect"
			data-id={i}
			x={$xScale.range()[0]}
			y={$yGet(d)}
			height={$yScale.bandwidth()}
			width={$xGet(d)}
			{fill}
		/>
	{/each}
</g>
