<template>
  <div class="calcContainer">
    <div class="calories">Calories: {{ calories }}</div>
    <form @submit.prevent="calculateCalories">
      <div>
        <label for="size">Choose size:</label>
        <select v-model="size" name="size" @change="calculateCalories">
          <option value="1">15 cm / 6"</option>
          <option value="2">30 cm / 12"</option>
        </select>
      </div>
      <div>
        <label for="bread">Choose bread:</label>
        <select
          v-model="selectedBread"
          name="bread"
          @change="calculateCalories"
        >
          <option disabled value="">Choose bread</option>
          <option
            v-for="(bread, key) in breads"
            :key="key"
            v-bind:value="bread"
          >
            {{ bread.english }}
          </option>
        </select>
      </div>
      <div>
        <label for="meat">Choose filling:</label>
        <select v-model="selectedMeat" name="meat" @change="calculateCalories">
          <option disabled value="">Choose filling</option>
          <option v-for="(meat, key) in meats" :key="key" v-bind:value="meat">
            {{ meat.english }}
          </option>
        </select>
      </div>
      <div>
        <label for="sauce">Choose sauce:</label>
        <select
          v-model="selectedSauce"
          name="sauce"
          @change="calculateCalories"
        >
          <option disabled value="">Choose sauce</option>
          <option
            v-for="(sauce, key) in sauces"
            :key="key"
            v-bind:value="sauce"
          >
            {{ sauce.english }}
          </option>
        </select>
      </div>
      <div>
        <label for="sauce2">Choose second sauce:</label>
        <select
          v-model="selectedSauceII"
          name="sauce2"
          @change="calculateCalories"
        >
          <option disabled value="">Choose sauce</option>
          <option
            v-for="(sauce, key) in sauces"
            :key="key"
            v-bind:value="sauce"
          >
            {{ sauce.english }}
          </option>
        </select>
      </div>
      <div>
        <label for="sauce3">Choose third sauce:</label>
        <select
          v-model="selectedSauceIII"
          name="sauce3"
          @change="calculateCalories"
        >
          <option disabled value="">Choose sauce</option>
          <option
            v-for="(sauce, key) in sauces"
            :key="key"
            v-bind:value="sauce"
          >
            {{ sauce.english }}
          </option>
        </select>
      </div>
      <div>
        <label for="cheese">Choose cheese:</label>
        <select
          v-model="selectedCheese"
          name="cheese"
          @change="calculateCalories"
        >
          <option disabled value="">Choose cheese</option>
          <option
            v-for="(cheese, key) in cheeses"
            :key="key"
            v-bind:value="cheese"
          >
            {{ cheese.english }}
          </option>
        </select>
      </div>
      <div>
        <label for="cheese">Choose extra cheese:</label>
        <select
          v-model="selectedCheeseII"
          name="cheeseII"
          @change="calculateCalories"
        >
          <option disabled value="">Choose cheese</option>
          <option
            v-for="(cheese, key) in cheeses"
            :key="key"
            v-bind:value="cheese"
          >
            {{ cheese.english }}
          </option>
        </select>
      </div>
    </form>
    <div class="disclaimer">
      This calculator gives only rough estimate of calories based on data
      publicly made available by subway group and should not be used as medical
      reference. Calculator might miss some menu items and some values might be
      outdated. Calculator is in no way associated with Subway Group.
    </div>
  </div>
</template>

<script>
export default {
  name: "Calculator",
  data() {
    return {
      selectedBread: { calories: 0 },
      selectedSauce: { calories: 0 },
      selectedSauceII: { calories: 0 },
      selectedSauceIII: { calories: 0 },
      selectedMeat: { calories: 0 },
      selectedCheese: { calories: 0 },
      selectedCheeseII: { calories: 0 },
      size: 1,
      calories: 0,
      lang: "en",
    };
  },
  props: {
    breads: Object,
    sauces: Object,
    cheeses: Object,
    meats: Object,
  },
  methods: {
    calculateCalories() {
      this.calories =
        (this.selectedBread.calories +
          this.selectedSauce.calories +
          this.selectedSauceII.calories +
          this.selectedSauceIII.calories +
          this.selectedMeat.calories +
          this.selectedCheese.calories +
          this.selectedCheeseII.calories) *
        this.size;
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
select {
  height: 40px;
  width: 300px;
  max-width: 80vw;
  border: 1px solid rgba(63, 158, 0, 1);
  cursor: pointer;
  font-size: 18px;
}
label {
  margin: 10px 0px 5px 0px;
  display: block;
  font-size: 20px;
}
.calcContainer {
  text-align: center;
  background: white;
  margin: 0 auto;
  padding: 30px 25px;
  opacity: 0.95;
  border: 8px solid rgba(63, 158, 0, 1);
  max-width: 100vw;
}
@media screen and (min-width: 900px) {
  .calcContainer {
    width: 400px;
  }
}
.calories {
  background: rgba(63, 158, 0, 1);
  color: white;
  height: 50px;
  line-height: 50px;
  padding: 0px 25px;
  display: inline-block;
  margin: 15px auto;
  border: 3px solid white;
  box-shadow: -1px -1px 0px 7px rgba(63, 158, 0, 1);
  font-size: 22px;
  font-weight: 700;
  text-transform: uppercase;
}
.disclaimer {
  font-size: 12px;
  text-align: center;
  margin-top: 50px;
}
</style>
