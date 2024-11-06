<template>
  <div class="page page--login" data-page="login">
    <!-- HEADER -->
    <TopBackVue back="/"></TopBackVue>

    <div class="login">
      <div class="login__content">
        <h2 class="login__title">Create an account</h2>
        <div class="login-form">
          <form id="LoginForm" method="post" @submit.prevent="signup">
            <div class="login-form__row">
              <label class="login-form__label">User ID</label>
              <input
                type="text"
                name="user_id"
                v-model="form.user_id"
                value=""
                class="login-form__input required"
              />
            </div>
            <div class="login-form__row">
              <label class="login-form__label">Username</label>
              <input
                type="text"
                name="username"
                v-model="form.username"
                value=""
                class="login-form__input required"
              />
            </div>
            <div class="login-form__row">
              <label class="login-form__label">Email</label>
              <input
                type="text"
                name="email"
                v-model="form.email"
                value=""
                class="login-form__input required email"
              />
            </div>
            <div class="login-form__row">
              <label class="login-form__label">Password</label>
              <input
                type="password"
                name="password"
                v-model="form.password"
                value=""
                class="login-form__input required"
              />
            </div>
            <div class="login-form__row">
              <input
                type="submit"
                name="submit"
                class="login-form__submit button button--main button--full"
                id="submit"
                value="SIGN UP"
              />
            </div>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { reactive } from "vue";
import axios from "axios";
import TopBackVue from "@/components/templates/inc/TopBack.vue";

import { useRouter } from "vue-router";
const router = useRouter();

const form = reactive({
  user_id: "",
  username: "",
  email: "",
  password: "",
});

const signup = async () => {
  // const form = {
  //   user_srl: localStorage.getItem("user_srl"),
  //   // token_name: "ETH",
  // };
  const res = await axios.post(
    "http://1.231.89.30:3000/users/account/signin",
    form
  );
  const resData = res.data;
  console.log("여기 맞아?");
  console.log(resData);
  if (resData == "success") {
    router.push("/login");
  }
};
</script>

<style lang="scss" scoped></style>
