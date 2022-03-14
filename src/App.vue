<template>
<div class="container">
    <div class="row">
      <div class="col-md-6 col-md-offset-3"> 
      <button class="btn btn-danger" @click="addNewItem"> New Item Add</button>
     
     <br>
     <ul class="list-group">
      <transition-group name="slide">
  <li :key="number" v-for="(number, index) in numberList"  class="list-group-item" 
  @click="removeItem(index)"> Number :  {{number}} </li>
  </transition-group>
  </ul>
  </div>
    </div>

  </div>

</template>

<script>
export default {

  data () {
    return {
      numberList: [ 1,2,3,4,5,6 ]
    }
  },
  methods:{
    addNewItem(){
      const position= Math.floor(Math.random() * this.numberList.length);
      this.numberList.splice(position,0,this.numberList.length + 1);

    },
     removeItem(index){
       this.numberList.splice(index,1);


    }
  }
}
</script>

<style>
.fade-enter{
opacity:0;
}

.fade-enter-active{
  transition: opacity 1s;

}
.fade-leave{
  
}
.fade-leave-active{
transition: opacity 1s;
opacity:0;
}

.slide-enter{
  opacity:0;
}

.slide-enter-active{
animation: slide-in 1s ease-out forwards;
transition: opacity 0.5s;

}
.slide-leave{
  
}
.slide-leave-active{
  animation: slide-out 1s ease-out forwards;
  transition: opacity 1s;
  opacity: 0;
  position: absolute;
}
.slide-move{
  transition: transform 1s;
}
@keyframes slide-in {
  from{
    transform: translateY(20px)
  }
  to {
    transform: translateY(0px)

  }
}

@keyframes slide-out {
  from{
    transform: translateY(0px)
  }
  to {
    transform: translateY(20px)

  }
}

</style>
