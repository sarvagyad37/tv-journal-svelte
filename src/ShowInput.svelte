<script>
    import { createEventDispatcher } from "svelte";
    const dispatch = createEventDispatcher();

    let title = '';
    let rating = 1;

    const onTitleChange = (e) => {
        title = e.target.value;
    }

    const onRatingSelect = (e) => {
        rating = e.target.value;
    }

    const submitShow = () => {
        if (title.length > 0) {
            dispatch('submitShow', { show: { title, rating } });

            title = '';
            rating = 1;
        }
    }

</script>

<div class="main">
<input 
    type="text" 
    placeholder="Show Title"
    value={title}
    on:keyup={onTitleChange}
/>

<select value={rating} on:change={onRatingSelect}>
    <option value={1}>1</option>
    <option value={2}>2</option>
    <option value={3}>3</option>
    <option value={4}>4</option>
    <option value={5}>5</option>
</select>

<button disabled={!title} on:click={submitShow}>
    Submit
</button>

</div>

<style>
    .main {
      width: 100%;
      display: flex;
    }
    .main input {
      flex: 1;
    }
    .main select {
      width: 75px;
      margin-right: 10px;
      margin-left: 10px;
    }
    .main button {
      width: 75px;
    }
</style>