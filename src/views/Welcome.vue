<template>
  <div class="welcome container">
    <p>Welcome</p>
    <div v-if="showLogin">
      <h2>Log In</h2>
      <LogInForm @login="enterChat" />
      <p>No account yet? <span @click="showLogin = false">Sign Up</span></p>
    </div>
    <div v-else="!showLogin">
      <h2>Sign Up</h2>
      <SignUpForm @signup="enterChat" />
      <p>Already registered? <span @click="showLogin = true">Log In</span> instead</p>
    </div>
    
  </div>
</template>

<script>
import SignUpForm from '@/components/SignUpForm'
import LogInForm from '@/components/LogInForm'
import { ref } from '@vue/reactivity'
import { useRouter } from 'vue-router'

export default {
  components: {
    SignUpForm,
    LogInForm
  },
  setup() {
    const showLogin = ref(true)
    const router = useRouter()

    const enterChat = () => {
      router.push({ name: 'Chatroom' })
    }

    return { showLogin, enterChat }
  }
}
</script>

<style>
.welcome {
  text-align: center;
  padding: 20px 0;
}
.welcome form {
  max-width: 300px;
  margin: 20px auto;
}
.welcome label {
  display: block;
  margin: 20px 0 10px;
}
.welcome input {
  width: 100%;
  
  padding: 10px;
  border-radius: 20px;
  border: 1px solid #eee;
  outline: none;
  color: #999;
  margin: 10px auto;
}
.welcome span {
  font-weight: bold;
  text-decoration: underline;
  cursor: pointer;
}
.welcome button {
  margin: 20px auto;
}
@media (max-width: 470px) {
  .welcome input {
    max-width: 80%;
  }
  .welcome p {
    font-size: 0.9rem;
    padding: 0 15px;
  }
}
</style>