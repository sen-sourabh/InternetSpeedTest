<template>
    <div>
        <detected-speed @network-type="handleNetworkIdentified" @network-speed="handleNetworkSpeed">
            <span slot="unknown">
                <div>{{ network }}/{{ speed }} Mbps <q-icon size="xs" name="trending_flat" /></div>
            </span>
            <span slot="slow">
                <div>{{ network }}/{{ speed }} Mbps <q-icon size="xs" name="arrow_downward" /></div>
            </span>
            <span slot="fast">
                <div>{{ network }}/{{ speed }} Mbps <q-icon size="xs" name="arrow_upward" /></div>
            </span>
        </detected-speed>
    </div>
</template>

<script>
import DetectedSpeed from 'vue-identify-network';

export default {
    name: "NetworkInfo",
    components: {
        DetectedSpeed
    },
    data() {
        return {
            network: 0,
            speed: 0
        }
    },
    methods: {
        handleNetworkIdentified(type) {
            this.network = type;
            console.log('connection type: ', type);
        },
        handleNetworkSpeed(speed) {
            this.speed = speed;
            console.log('downlink: ', speed);
        }
    }
};
</script>