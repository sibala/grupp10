<script setup lang="ts">
import { ref } from "vue";
import LoginForm from "@/components/LoginForm.vue";
import RegisterForm from "@/components/RegisterForm.vue";
import BackButton from "@/components/BackButton.vue";

// Show Login be default
const showLogin = ref(true);

// Switch to registerform
function switchToRegister() {
  showLogin.value = false;
}

// Switch to registerform
function switchToLogin() {
  showLogin.value = true;
}
</script>

<template>
  <BackButton to="/" />
  <div>
    <transition name="fade" mode="out-in">
      <!-- Show login form if showLogin is true, else show register form -->
      <LoginForm v-if="showLogin" @switch-to-register="switchToRegister" />
      <RegisterForm v-else @switch-to-login="switchToLogin" />
    </transition>
  </div>
</template>

<style scoped>
.auth-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1rem;
}

.auth-toggle {
  display: flex;
  gap: 1rem;
}

.auth-toggle button {
  padding: 0.5rem 1rem;
  cursor: pointer;
}

.auth-toggle .active {
  font-weight: bold;
  background-color: #ddd;
}
</style>
