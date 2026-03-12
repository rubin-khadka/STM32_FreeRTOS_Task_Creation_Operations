# STM32 FreeRTOS Task Creation and Operations

Simple code testing FreeRTOS on STM32. Started Default Task and Task 2 using CubeMX, started Task 3 using code. All tasks send messages to UART1 which can be viewed using serial monitor.

## Tasks Overview
| Task | Priority | Behavior |
|------|----------|----------|
| Default Task | Normal | Prints "Default Task" every 1 second |
| Task 2 | AboveNormal | Prints index count every 2 seconds |
| | | Suspends Default Task at index 4 |
| | | Resumes Default Task at index 7 |
| Task 3 | BelowNormal | Prints "Hello from Task 3" every 3 seconds |
| | | At count 3: uses osDelayUntil for 3 sec delay |
| | | At count 7: terminates Task 2 |

## FreeRTOS Functions Used
- `osThreadCreate` - Create tasks (CubeMX vs manual)
- `osThreadSuspend` - Suspend Default Task
- `osThreadResume` - Resume Default Task  
- `osThreadTerminate` - Terminate Task 2
- `osDelay` - Relative delay
- `osDelayUntil` - Absolute/periodic delay

## Other FreeRTOS Functions (Not in this code)
There are many other functions like:
- `osThreadSuspendAll` / `osThreadResumeAll` - Suspend/resume all tasks
- `osThreadGetPriority` / `osThreadSetPriority` - Get/set task priority
- `osThreadYield` - Force task switch
- `osThreadGetId` - Get current task handle

## Code Contains
- **Task Creation**: Two methods - CubeMX GUI (Default/Task2) vs manual code (Task3)
- **Task Control**: suspend, resume, and terminate operations
- **Timing**: Regular osDelay vs osDelayUntil for precise timing
- **Priority**: AboveNormal, Normal, and BelowNormal priorities showing preemption