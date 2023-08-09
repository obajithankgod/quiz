<template>
  <div class="ctr">
    <transition name="fade" mode="out-in">
      <QuestionComp
        v-if="questionsAnswered < questions.length"
        :questions="questions"
        :questionsAnswered="questionsAnswered"
        @question-answered="questionAnswered"
      />
      <ResultComp v-else :results="results" :totalCorrect="totalCorrect" />
    </transition>

    <button
      type="button"
      class="reset-btn"
      @click.prevent="reset"
      v-if="this.questionsAnswered === questions.length"
    >
      Next
    </button>
  </div>
</template>

<script>
import ResultComp from "./components/ResultComp.vue";
import QuestionComp from "./components/QuestionComp.vue";
export default {
  name: "App",
  components: {
    QuestionComp,
    ResultComp,
  },
  data() {
    return {
      questionsAnswered: 0,
      totalCorrect: 0,
      questions: [
        {
          q: "What is 2 + 2?",
          answers: [
            {
              text: "4",
              is_correct: true,
            },
            {
              text: "3",
              is_correct: false,
            },
            {
              text: "8",
              is_correct: false,
            },
            {
              text: "5",
              is_correct: false,
            },
          ],
        },
        {
          q: 'How many letters are in the word "Banana"?',
          answers: [
            {
              text: "5",
              is_correct: false,
            },
            {
              text: "7",
              is_correct: false,
            },
            {
              text: "6",
              is_correct: true,
            },
            {
              text: "12",
              is_correct: false,
            },
          ],
        },
        {
          q: "Find the missing letter: C_ke",
          answers: [
            {
              text: "e",
              is_correct: false,
            },
            {
              text: "a",
              is_correct: true,
            },
            {
              text: "i",
              is_correct: false,
            },
          ],
        },
        {
          q: "What is the acronym HTML stand for?",
          answers: [
            {
              text: "HyperText Markup Language",
              is_correct: true,
            },
            {
              text: "How to makeup language",
              is_correct: false,
            },
            {
              text: "How to make language",
              is_correct: false,
            },
          ],
        },
        {
          q: "What is a Components in vuejs",
          answers: [
            {
              text: "Component are reusable vue instances with custom HTML element",
              is_correct: true,
            },
            {
              text: "Component are reusable pies of html code ",
              is_correct: false,
            },
            {
              text: "Component can not be use as many times",
              is_correct: false,
            },
          ],
        },
        {
          q: "fine the missing letter in the word Devel_pment",
          answers: [
            {
              text: "e",
              is_correct: false,
            },
            {
              text: "o",
              is_correct: true,
            },
            {
              text: "u",
              is_correct: false,
            },
          ],
        },
      ],
      results: [
        {
          min: 0,
          max: 2,
          title: "Try again!",
          desc: "Do a little more studying and you may succeed!",
        },
        {
          min: 3,
          max: 6,
          title: "Wow, congrats you're a genius!",
          desc: "Studying has definitely paid off for you",
        },
      ],
    };
  },
  methods: {
    questionAnswered(is_correct) {
      if (is_correct) {
        this.totalCorrect++;
      }
      this.questionsAnswered++;
    },
    reset() {
      this.questionsAnswered = 0;
      this.totalCorrect = 0;
    },
  },
};
</script>

<style></style>

