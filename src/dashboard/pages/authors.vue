<template>
    <div>
        <h1>Authors</h1>
        <div class="mb-2">
            <b-button variant="success" @click="addAuthor">Add Author</b-button>
        </div>
        <AuthorTable :authors-data="authors"></AuthorTable>
    </div>
</template>

<script>
import AuthorTable from '~/components/AuthorTable.vue';

export default {
    data() {
        return {
            authors: [],
        };
    },
    async asyncData({ store }) {
        // Fetch the list of authors from the backend using Vuex actions
        await store.dispatch('fetchAuthors');
        return {
            authors: store.state.authors.authors,
        };
    },
    methods: {
        addAuthor() {
            // Redirect to the page where you can add a new author
            this.$router.push('/add-author');
        },
    },
    components: { AuthorTable },
};
</script>
