<template>
    <form @submit.prevent="onSave">
        <h1>Add new Post</h1>
        <AppControlInput v-model="editedPost.author">Author Name</AppControlInput>
        <AppControlInput v-model="editedPost.title">Title</AppControlInput>
        <AppControlInput v-model="editedPost.thumbnail">Thumbnail Link</AppControlInput>
        <AppControlInput
                control-type="textarea"
                v-model="editedPost.content">Content</AppControlInput>
        <AppControlInput
                control-type="textarea"
                v-model="editedPost.previewText">Preview Text</AppControlInput>
            
        <AppButton type="submit">Save Post</AppButton>
        <AppButton
            type="button"
            style="margin-left: 10px"
            btn-style="cancel"
            @click="onCancel">Cancel</AppButton>
    </form>
</template>


<script>
export default {
    props:{
        post:{
            type: Object,
            required: false
        }
    },
    data(){
        return{
            // when props are available then display props otherwise dispaly blank given below
            editedPost: this.post ? { ...this.post } : {
                author: "",
                title:"",
                thumbnail:"",
                content:"",
                previewText:""
            }
        }
    },
    methods:{
        onSave(){
            // console.log(this.editedPost)
            this.$emit('submit', this.editedPost)
        },
        onCancel(){
            this.$router.push('/admin');
        }
    }
}
</script>