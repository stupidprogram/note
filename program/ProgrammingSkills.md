#Table-Driven Method
according to three enumerates that had defined:module type, message type, its own module status,then define a function jump table:
```c
typedef struct  __EVENT_DRIVE  
{  
    MODE_TYPE mod;//message sending module  
    EVENT_TYPE event;//message type
    STATUS_TYPE status;//self status  
    EVENT_FUN eventfun;//function pointer in this status
}EVENT_DRIVE;  

EVENT_DRIVE eventdriver[] = //this is just one of the definition of the table, it may not be the table of the database,you can also define you arrays of structure of yourself.   
{  
    {MODE_A, EVENT_a, STATUS_1, fun1}  
    {MODE_A, EVENT_a, STATUS_2, fun2}  
    {MODE_A, EVENT_a, STATUS_3, fun3}  
    {MODE_A, EVENT_b, STATUS_1, fun4}  
    {MODE_A, EVENT_b, STATUS_2, fun5}  

    {MODE_B, EVENT_a, STATUS_1, fun6}  
    {MODE_B, EVENT_a, STATUS_2, fun7}  
    {MODE_B, EVENT_a, STATUS_3, fun8}  
    {MODE_B, EVENT_b, STATUS_1, fun9}  
    {MODE_B, EVENT_b, STATUS_2, fun10}  
};  

int driversize = sizeof(eventdriver) / sizeof(EVENT_DRIVE)//the size of the driven table  

EVENT_FUN GetFunFromDriver(MODE_TYPE mod, EVENT_TYPE event, STATUS_TYPE status)//search function of the driven table
{  
    int i = 0;  
    for (i = 0; i < driversize; i ++)  
    {  
        if ((eventdriver[i].mod == mod) && (eventdriver[i].event == event) && (eventdriver[i].status == status))  
        {  
            return eventdriver[i].eventfun;  
        }  
    }  
    return NULL;  
}  
```
the benefits of this method:</br>
1. It improve the readability of the program.</br>
2. It reduced the duplication of the code.</br>
3. Scalability.</br>
4. The program has a distinct backbone.
5. It reduced the complexity.
