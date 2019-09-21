<template>
    <div class="tasks-grid">
        <template v-if="tasks.length">
            <Task
                v-for="(task, i) in tasks"
                :key="task.name"
                :task="task"
                @taskStateChanged="$emit('taskStateChanged', i)"
                @taskDeleted="$emit('taskDeleted', i)" />
        </template>
        <p v-else class="no-task">Sua vida está em dia :)</p>
    </div>
</template>

<script>
    import Task from './Task';

    export default {
        name: 'TaskGrid',
        props: {
            tasks: { type: Array, required: true }
        },
        components: { Task }
    }
</script>

<style scoped>
    .tasks-grid {
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
    }

    .tasks-grid .task {
        margin: 10px;
    }

    .no-task {
        color: #aaa;
        font-size: 1.7rem;
    }
</style>