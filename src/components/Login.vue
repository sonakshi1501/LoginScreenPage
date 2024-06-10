<template>
    <v-app>
      <v-main>
        <v-container class="fill-height" fluid>
          <v-row class="fill-height" justify="center" align="center">
            <v-col cols="12" sm="8" md="4">
              <v-card class="elevation-10 pa-8 rounded-lg login-card">
                <v-card-title class="headline text-center">Login</v-card-title>
                <v-card-text>
                  <v-form ref="form" v-model="valid">
                    <v-text-field
                      v-model="username"
                      label="Username"
                      prepend-icon="mdi-account"
                      outlined
                      :rules="usernameRules"
                      required
                    ></v-text-field>
                    <v-text-field
                      v-model="password"
                      label="Password"
                      prepend-icon="mdi-lock"
                      outlined
                      type="password"
                      :rules="passwordRules"
                      required
                    ></v-text-field>
                    <v-btn text class="mt-2" color="primary">Forgot password?</v-btn>
                  </v-form>
                </v-card-text>
                <v-card-actions class="justify-center">
                  <v-btn
                    :disabled="!valid"
                    class="gradient-button"
                    @click="login"
                  >
                    Login
                  </v-btn>
                </v-card-actions>
                <v-card-actions class="justify-center">
                  <div class="mt-2">Or Sign Up Using</div>
                </v-card-actions>
                <v-card-actions class="justify-center">
                  <v-btn icon><v-icon color="blue darken-3">mdi-facebook</v-icon></v-btn>
                  <v-btn icon><v-icon color="blue lighten-1">mdi-twitter</v-icon></v-btn>
                  <v-btn icon><v-icon color="red darken-3">mdi-google</v-icon></v-btn>
                </v-card-actions>
                <v-card-actions class="justify-center">
                  <div class="mt-2">Or Sign Up Using</div>
                </v-card-actions>
                <v-card-actions class="justify-center">
                  <v-btn text class="mt-2" color="primary">SIGN UP</v-btn>
                </v-card-actions>
              </v-card>
            </v-col>
          </v-row>
        </v-container>
      </v-main>
    </v-app>
  </template>
  
  <script>
  export default {
    data() {
      return {
        username: '',
        password: '',
        valid: false,
        usernameRules: [
          v => !!v || 'Username is required',
        ],
        passwordRules: [
          v => !!v || 'Password is required',
          v => v.length >= 6 || 'Password must be at least 6 characters',
        ],
      };
    },
    methods: {
      login() {
        if (this.$refs.form.validate()) {
          // Perform login logic here
          console.log('Username:', this.username);
          console.log('Password:', this.password);
        }
      },
    },
  };
  </script>
  
  <style scoped>
  .fill-height {
    min-height: 100vh;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  }
  
  .login-card {
    background-color: white;
    border-radius: 10px;
  }
  
  .gradient-button {
    background: linear-gradient(90deg, #00C9FF 0%, #92FE9D 100%);
    color: white;
    border-radius: 20px;
    text-transform: uppercase;
    font-weight: bold;
  }
  
  .v-icon {
    font-size: 24px;
  }
  </style>