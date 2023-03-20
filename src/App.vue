<template>
 
   <section class="vh-100 bg-image"
  style="background-image: url('https://mdbcdn.b-cdn.net/img/Photos/new-templates/search-box/img4.webp');">
  <div class="mask d-flex align-items-center h-100 gradient-custom-3">
    <div class="container h-100">
      <div class="row d-flex justify-content-center align-items-center h-100">
        <div class="col-12 col-md-9 col-lg-7 col-xl-6">
          <div class="card" style="border-radius: 15px;">
            <div class="card-body p-5">
              <h2 class="text-uppercase text-center mb-5">Create an account</h2>

              <form>

                <div class="form-outline mb-4">
                  <input type="text" id="name-input" v-model.lazy="name" @blur="checkname" class="form-control form-control-lg" />
                  <label class="form-label" for="name-input">Your Name</label>
                  <div v-if="!isnamevalid && nameEntered" class="error" >Please enter a valid name</div>
                </div>

                <div class="form-outline mb-4">
                  <input type="email" id="email-input" v-model.lazy="email" @blur="checkemail" class="form-control form-control-lg" />
                  <label class="form-label" for="email-input">Your Email</label>
                  <div v-if="!isemailvalid && emailEntered" class="error" >Please enter a valid Email</div>
                </div>

                <div class="form-outline mb-4">
            
                   <input type="password" v-model="password" @input="checkPassword" @blur="passwordEntered= true" class="form-control form -control-lg">
                    <label class="form-label" for="password-input">Password</label>
                  <p v-if="passwordEntered && !ispasswordvalid" class="error">{{ passwordError }}</p>
                
                </div>

                <div class="form-outline mb-4">
                    <input type="number" id="number-input" v-model.lazy="number" @blur="checknumber" class="form-control form-control-lg" />
                  <label class="form-label" for="number-input">Your phonenumber</label>
                  
                  <p v-if=" numberEntered && !isnumbervalid " class="error" >Please enter a valid Number</p>
                  
                      </div>

                

                <div class="d-flex justify-content-center">
                  <button type="button" :disabled="!isformvalid" @click="submitform"
                    class="btn btn-success btn-block btn-lg gradient-custom-4 text-body" >Submit</button>
                </div>

                <p class="text-center text-muted mt-5 mb-0">Have already an account? <a href="#!"
                    class="fw-bold text-body"><u>Login here</u></a></p>

              </form>

            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>
</template>

<script>


export default {
  data(){
    return{
        name:'',
       email:'',
        password:'',
        number:'',
       nameEntered:false,
       emailEntered:false,
       passwordEntered:false,
       numberEntered:false,
       formsubmitted:false
     
      
    }
  },
  methods:{
   checkname(){
    this.nameEntered=true;
   },
   checkemail(){
    this.emailEntered=true;
   },
   checkpassword(){
    this.passwordEntered=true;
   },
 checknumber(){
  this.numberEntered=true;
 },

  
   
    submitform() {
      this.formsubmitted = true;
  
      alert('Form Submitted Sucessfully');

  }
  },
  
   computed: {
    isnamevalid() {
      const nameRegex = /^[a-zA-Z ]{2,30}$/; 
      return nameRegex.test(this.name);
    },
    isemailvalid() {
      const emailRegex = /^\S+@\S+\.\S+$/; 
      return emailRegex.test(this.email);
    },
    ispasswordvalid() {
      const passwordRegex = /^(?=.*[a-z])(?=.*[A-Z])(?=.*\d)(?=.*[^\da-zA-Z]).{8,}$/;
      return passwordRegex.test(this.password);
    },
     passwordError() {
      if (!this.password) {
        return 'Please enter a password';
      } else if (this.password.length < 8) {
        return 'Password must be at least 8 characters long';
      } else if (!/[a-z]/.test(this.password)) {
        return 'Password must contain at least one lowercase letter';
      } else if (!/[A-Z]/.test(this.password)) {
        return 'Password must contain at least one uppercase letter';
      } else if (!/\d/.test(this.password)) {
        return 'Password must contain at least one number';
      } else if (!/[^\da-zA-Z]/.test(this.password)) {
        return 'Password must contain at least one special character';
      } else {
        return '';
      }
    },
    isnumbervalid() {
      const nameRegex =/^\(?([0-9]{3})\)?[-.●]?([0-9]{3})[-.●]?([0-9]{4})$/; 
      return nameRegex.test(this.number);
    },
    
   
    
    isformvalid() {
  return this.isnamevalid && this.isemailvalid && this.ispasswordvalid && this.isnumbervalid;
}


}
}
</script>

<style>
.gradient-custom-3 {

background: #84fab0;


background: -webkit-linear-gradient(to right, rgba(132, 250, 176, 0.5), rgba(143, 211, 244, 0.5));


background: linear-gradient(to right, rgba(132, 250, 176, 0.5), rgba(143, 211, 244, 0.5))
}
.gradient-custom-4 {

background: #84fab0;

background: -webkit-linear-gradient(to right, rgba(132, 250, 176, 1), rgba(143, 211, 244, 1));


background: linear-gradient(to right, rgba(132, 250, 176, 1), rgba(143, 211, 244, 1))
}
.error {
  color: red;
}
</style>
