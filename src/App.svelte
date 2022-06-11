<script>
	let firstName = 'Louis'
	let lastName = 'Leonardo'
	let color = 'blue'
	let showText = false
	let users = [
		{
			id:'1',
			name:'John'
		},
		{
			id:'2',
			name:'Sara'
		}
	]

	const toggle = () => {
		color = color === 'blue' ? 'red':'blue'
		showText = !showText
		users = [...users,{id:'4',name:'Jen'}]
	}

	$: name = firstName + ' ' + lastName	// reactive variable whenever this change will update automatically
</script>

<main>
	<h1 style="color: {color}">Hello {name}!</h1>
	{#if showText}
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
	{:else}
		<p>no Text</p>
	<!-- <button on:click={()=> color = 'purple'}></button> -->
	{/if}

	{#each users as users(users.id)}
		<h3>{users.id}:{users.name}</h3>
	{/each}
	<button on:click={toggle}>Click</button>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>