<template>
    <section>

        <section class="snackbar" @click="close">
            <figure class="icon" v-if="item.icon">
                <i :class="`icon-${item.icon}`"></i>
            </figure>
            <figure class="message" :class="{'no-icon':!item.icon}">{{item.message}}</figure>
        </section>

    </section>
</template>

<script>
    import { mapActions, mapGetters, mapState } from 'vuex'
    import * as Actions from '../../../store/constants';

    export default {
        computed:{
            item(){
                return this.popup.data.props;
            }
        },
        methods:{
            close(){
                this[Actions.RELEASE_POPUP](this.popup)
            },
            ...mapActions([
                Actions.RELEASE_POPUP
            ])
        },
        props:['popup']
    }
</script>

<style scoped lang="scss" rel="stylesheet/scss">
    @import "../../../variables";

    .snackbar {
        cursor: pointer;

        display:inline-block;

        margin-top:10px;

        background:$light-blue;
        background-image: linear-gradient(-180deg, #62D0FD -20%, #39ADFF 100%);

        color:white;
        padding:10px 0;
        border-radius:40px;
        box-shadow:0 6px 28px rgba(0,0,0,0.12);
        border:1px solid $light-blue;
        text-align:left;

        .icon {
            display:inline-block;
            padding:0 10px;

            i {
                display:inline-block;
                height:30px;
                width:30px;
                line-height:30px;
                text-align:center;
                background:white;
                border-radius:50%;
                color:$dark-grey;
                font-size:16px;
                box-shadow:0 2px 3px rgba(0,0,0,0.2);
            }
        }

        .message {
            vertical-align: middle;
            display:inline-block;
            padding-right:20px;
            padding-bottom:3px;
            color:white;
            font-size:13px;
            font-weight: bold;

            &.no-icon {
                padding:0 20px;
            }

        }
    }

</style>