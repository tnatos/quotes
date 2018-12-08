<template>
    <div class="container">
      <app-quotes-added-bar :quoteCount="quotes.length" :maxQuotes="maxQuotes"/>
      <app-quote-input @quoteAdded="addQuote($event)"/>
      <app-quote-area :quotes="quotes" @quoteRemoved="removeQuote($event)"/>
      <app-footer/>
    </div>
</template>

<script>
    import QuoteArea from './components/QuoteArea.vue';
    import QuoteInput from './components/QuoteInput.vue';
    import QuotesAddedBar from './components/QuotesAddedBar.vue';
    import Footer from './components/Footer.vue';
    export default {
      data: function() {
        return {
          quotes: ['quote 1',],
          maxQuotes: 10
        }
      },
      methods: {
        addQuote(quote) {
          if(this.quotes.length < this.maxQuotes) {
            this.quotes.push(quote);
          }
          else {
            alert('Cannot add any more quotes!');
          }
        },
        removeQuote(index) {
          console.log(index);
          this.quotes.splice(index, 1);
        }
      },
      components: {
        'app-quote-area': QuoteArea,
        'app-quote-input': QuoteInput,
        'app-quotes-added-bar': QuotesAddedBar,
        'app-footer': Footer
      }
    }
</script>

<style scoped>
</style>
