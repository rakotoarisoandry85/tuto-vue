<script setup>
import {computed, ref} from 'vue'
import Card from './components/Card.vue';
//import Button from './components/Button.vue';
  const count = ref(0)
  const html = '<span> Une page HTML...</span>'
  const list = ref(
    {
      lastName:'John',
      firstName:'Doe',
      age:25,
    }
  )
  //tableau de personnes
  const personnes = ref([
    {
      id:1,
      name:'John',
    },  
    {
      id:2,
      name:'Jane',
    },  
    {
      id:3,
      name:'Jihane',
    },  
  ])
  const username = ref('')
  // function incremente(){
  //   console.log('clic...');
  //   return count.value++
  // }
  const incremente = ()=> count.value++
  // function decremente(){
  //   //console.log('clic...');
  //   return count.value--
  // }
  const decremente = ()=> count.value--
  // function updateAge(){
  //   //console.table(list)
  //   return list.value.age++
  // }
  const updateAge = ()=> list.value.age++ 
  // function deletePersonne(id){
  //   return personnes.value = personnes.value.filter(p=>p.id!==id)
  // }
  const deletePersonne = (id)=> personnes.value = personnes.value.filter(p =>p.id!==id)
  const setId = (id)=> id+1
  const addPersonne = ()=> {
    const lastElement = personnes.value.at(-1);
    personnes.value.push({
      id:setId(lastElement.id),
      name:username.value})  
    }
</script>

<template>
  <h1 class="text-3xl font-bold text-blue-600 text-center mt-10">
    Tuto Vue js !
  </h1>
  <!-- <p class="flex items-center mt-4">
    Visit <a href="https://vuejs.org/" target="_blank" rel="noopener">vuejs.org</a> to read the
    documentation
  </p> -->
  <div class="flex items-center justify-center gap-2.5 ">
    <p style="color: blueviolet;"> Valeur de Count est {{ count }} </p>
    
    <p style="color: blueviolet;"> l'age de {{ list.lastName }}  {{ list.firstName }}  est {{ list.age }} </p>
  </div> 
  <div class="flex items-center justify-center  ">
    <form action=""  @submit.prevent="addPersonne"  class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4">
      <div class="mb-4">
        <label class="block text-gray-700 text-sm font-bold mb-2" for="username">
          Ajoute un nom
        </label>
        <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
          
         type="text" 
         v-model="username"
         placeholder="Username">
      </div>
      <div class="flex items-center justify-between">
      <button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline" type="submit">
        Ajouter
      </button>
   
    </div>
    </form>
  </div> 
  <hr>
    <div class="flex items-center gap-3.5 mt-5">
              
    <!-- <div v-show="count>=5"> 
        Vous avez cliqué 5 fois!
    </div>  -->

    <!-- <div v-if="count>=5"> Vous avez cliqué {{ count }} fois</div>
    <div v-else="count<=5"> Vous avez cliqué {{ count }} fois</div>
      -->
      <p :class="{active:count>5}"> Compteur de {{ count }}</p>    <!-- on ajoute une class dynamique avec le : avant class -->

      <div v-html="html"></div>

      <buton  style="" class="inline-flex items-center py-2 px-3 text-sm font-medium text-center text-white bg-blue-700 rounded-lg hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
              @:click.prevent="incremente">
        Clic me to incremente           
      </buton>

      <buton  style="" class="inline-flex items-center py-2 px-3 text-sm font-medium text-center text-white bg-blue-700 rounded-lg hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
              @:click.prevent="decremente">
        Clic me to decremente          
      </buton>

      <button class="inline-flex items-center py-2 px-3 text-sm font-medium text-center text-white bg-blue-700 rounded-lg hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800" v-on:click.prevent="updateAge">
        update age...
      </button>

      <!-- <li>
        <ul v-for="personne in personnes"> {{ personne }}</ul>
      </li> -->

    </div>
  <hr class="mt-10">
  <section class="mt-5">
    <ul class="ml-15">
      <li v-for="pers in personnes" :key="pers.id" :name="pers.name"> {{ pers.name }} <button class="inline-flex items-center py-2 px-3 text-sm font-medium text-center text-white bg-blue-700 rounded-lg hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
         :key="pers.id"
         @click="deletePersonne(pers.id)"
         > Supprimer </button> </li>
      
    </ul>
  </section>

  <!-- carte -->
<!-- <div class="flex items-center gap-5">
  <Card v-for="personne in personnes" :key="personne.id" :name="personne.name"/> 
</div> -->
   
</template>

<style scoped>
.active{
  color: red;
}
</style>
