<template>
    <section>FILTER</section>
    <section>
        <base-card>
            <div class="controls">
                <base-button mode="outline">refresh</base-button>
                <base-button link="true" to="/register">Register as Coach</base-button>
            </div>
            <ul v-if="hasCoaches">
            <coach-item 
                v-for="coach in filteredCoaches"
                v-bind:key="coach.id"
                v-bind:id="coach.id"
                v-bind:first-name="coach.firstName"
                v-bind:last-name="coach.lastName"
                v-bind:rate="coach.hourlyRate"
                v-bind:areas="coach.areas"
            >              
            </coach-item>  
            </ul>
            <h3 v-else> no coaches found. </h3>
        </base-card>
    </section>
</template>



<script>

import CoachItem from '../../components/coaches/CoachItem.vue';

export default {
    components: {
        CoachItem
    },
    computed: {
        filteredCoaches() {
            return this.$store.getters['coaches/coaches'];
        },
        hasCoaches() {
           return this.$store.getters['coaches/hasCoaches']; 
        }
    }
}
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
}

.controls {
  display: flex;
  justify-content: space-between;
}
</style>