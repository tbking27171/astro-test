<script>
	let dogs = [];
	let newDog = null;

	function addDog() {
		if (!newDog) return;

		dogs = [...dogs,
			{
				id: new Date(),
				name: newDog
			}
		];

		newDog = null;
	}

  function handleSubmit(e) {
    e.preventDefault();
  }

	function removeDog(index) {
		const newDogs = [...dogs];
		newDogs.splice(index, 1);
		dogs = newDogs;
	}
</script>

<div class="title">
	<h1>Svelte</h1>
	<span>
		Tareas <strong>{dogs.length}</strong>
	</span>
</div>
{#if (dogs.length >= 10)}
	<div class="msj">
		<p>¡Wow ya 10 tareas!</p>
	</div>
{/if}
<ul>
	{#each dogs as {id, name} }
		<li key={id}>
			{name}
      <button on:click={removeDog} class="remove">X</button>
    </li>
	{/each}
</ul>

<form on:submit={handleSubmit}>
  <input type="text" bind:value={newDog} placeholder="Add" />
  <button on:click={addDog} class="add">Add a Dog</button>
</form>

<style></style>