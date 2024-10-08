<script setup>
import { reactive, watch } from 'vue';
import AuthenticationService from '@/services/AuthenticationService';

const form = reactive({
    email: '',
    password: '',
});



const register = async () => {
    try {
        const response = await AuthenticationService.register({
            email: form.email,
            password: form.password
        });
        console.log(response.data);
    } catch (error) {
        console.error(error);
    }
}

</script>

<template>
    <div class="flex items-center justify-center min-h-screen">
        <div class="bg-white p-8 rounded shadow-lg">
            <h2 class="text-center text-2xl font-bold mb-4">Register</h2>
            <form @submit.prevent="register">
                <div class="mb-4">
                    <label for="email" class="block mb-2">Email</label>
                    <input v-model="form.email" type="email" name="email" id="email" class="border w-full p-2" placeholder="Email" />
                </div>
                <div class="mb-4">
                    <label for="password" class="block mb-2">Password</label>
                    <input v-model="form.password" type="password" name="password" id="password" class="border w-full p-2" placeholder="Password" />
                </div>
                <div class="flex justify-center">
                    <button type="submit" class="bg-blue-500 text-white px-4 py-2 rounded hover:bg-blue-700 transition">
                        Submit
                    </button>
            </div>
            </form>
        </div>
    </div>
</template>