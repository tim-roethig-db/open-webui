<script>
	import { onMount } from 'svelte';
	import { models } from '$lib/stores';
	import { getModels } from '$lib/apis';
	import { base } from '$app/paths';
	import Models from '$lib/components/workspace/Models.svelte';

	onMount(async () => {
		await Promise.all([
			(async () => {
				models.set(await getModels(localStorage.token));
			})()
		]);
	});
</script>

{#if $models !== null}
	<Models />
{/if}
