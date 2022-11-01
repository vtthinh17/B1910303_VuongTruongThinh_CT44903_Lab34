<template>
     <div class="page">
        <h4>Thêm mới liên hệ Liên hệ</h4>
        <ContactForm 
        :contact="contact" 
        @submit:contact="addContact" 
        />
        <p>{{ message }}</p>
    </div>
</template>
<script>
import ContactForm from "@/components/ContactForm.vue";
import ContactService from "./../services/contact.service";
export default {
    // Dang ky component de su dung tren template
    components: {
        ContactForm,
    },
    // props: {
    //     // contact: { type: Object, required: true },
    // },
    data() {
        return {
            contact: {},
            message: "",
        };
    },
    methods: {
        async addContact(data) {
            try {
                await ContactService.create(data);
                this.message = "Liên hệ được thêm thành công.";
                // this.$router.push({ name: "contactbook" });
            } catch (error) {
                console.log(error);
            }
        },
    },
    created() {

        this.message = "";
    },
};
</script>
