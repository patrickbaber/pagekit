<template>

    <div class="uk-form-select pk-filter">
        <span>{{ label }}</span>
        <select v-if="isNumber" v-model="value" options="list" number></select>
        <select v-if="!isNumber" v-model="value" options="list"></select>
    </div>

</template>

<script>

    module.exports = {

        props: ['title', 'value', 'options', 'number'],

        computed: {

            isNumber: function() {
                return this.number !== undefined;
            },

            list: function() {
                return [{value: '', text: this.title }].concat(this.options);
            },

            label: function () {
                var list = this.list.concat(_.flatten(_.pluck(this.list, 'options')));
                var value = _.find(list, 'value', this.value);
                return value ? value.text : this.title;
            }

        }

    };

</script>
