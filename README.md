# yaseen
Demo


Threads and MultiThreading


* A Thread is an independent part of same program which will get its own
  stack and CPU time for the execution.
  
* Threads are used for performing MULTITASKING in programs / applications.

* Thread creation and execution is a costly with respect to memory and CPU time
  and hence unwanted thread creations should totally avoided.
  
* Whenever JVM starts the execution it creates 3 threads by default
  
  Main thread
  Garbage collector
  Thread Scheduler
  
* By default all the programs in java will be executed in Main Thread.

* In java threads can be created in 2 ways
  - By Extending Thread class
  - By Implementing Runnable interface
  
  
 * By Extending Thread class
 
   * Define task
     Step 1: Create a class that extends Thread class.
     Step 2: Override run() to define the task that should be executed by the thread.
     
   * Start the thread execution
     Step 3: Create the object of Subclass
     Step 4: Use the subclass object to call start() of Thread class.
 
 
 * By Implementing Runnable interface
   
   * Define task
     Step 1: Create a class that implements Runnable interface.
     Step 2: Override run() to define the task that should be executed
             by the thread.
   
   * Start the thread execution
     Step 3: Create the object of implementation class
     Step 4: Create the Object of Thread class and pass the implementation class
             object reference to Thread constructor.
     Step 5: Use the Thread class object to call start() of Thread class.
   
   
   * If the class is already extends from some other superclass , then
     its is not possible to extends Thread class as it leads multiple
     inheritance and hence thread task is define by Implementing Runnable interface.
 
 
 Executor Framework
 
  Executor Framework helps in creating and managing Thread groups/pools.
 
  * We can reuse same thread to perform new task.
  * Threads will execute asynchronous.
  * We can control the start and stop of thread execution explicitly.
  * For every type of requirement different pre-defined pools are avilable.
  
  * Executor framework will seperate Task and thread creation.
  
  * 1. Define the task 
    2. Create thread pool
    3. Submit the task
    
    
    * There are 4 different types of pools that can be created using
      Executor framework
      
      1. Fixed Thread Pool
      2. Cached Thread Pool
      3. Scheduled Thread pool
      4. Single thread executor
    
    
  Fixed Thread Pool
  * Creates a thread pool that reuses a fixed number of threads 
    operating off a shared unbounded queue. 
  
  * At any point, at most nThreads threads will be active processing tasks.
  
  * If additional tasks are submitted when all threads are active,
    they will wait in the queue until a thread is available.
  
  * If any thread terminates due to a failure during execution 
    prior to shutdown,a new one will take its place if needed to 
    execute remaining tasks.
 
  * The threads in the pool will exist until it is explicitly shutdown.
    
    
    Cached Thread Pool
    
   * Creates a thread pool that creates new threads as needed, 
     but will reuse previously constructed threads when they 
     are available. 
   
   * These pools will typically improve the performance of programs
     that execute many short-lived asynchronous tasks.
    
   * Calls to execute will reuse previously constructed threads if available. 
    
   * If no existing thread is available, a new thread will be created and added
     to the pool. 
     
   * Threads that have not been used for sixty seconds are 
     terminated and removed from the pool. 
    
     Thus, a pool that remains idle for long enough will not consume any 
     resources.
    
    
   Scheduled Thread pool
    
  * A thread pool that can schedule tasks to run after a
    given delay, or to execute periodically.
    
  * This thread pool reuses a fixed number of threads 
    operating off a shared unbounded queue. 
  
  * At any point, at most nThreads threads will be active processing tasks.
  
  * If additional tasks are submitted when all threads are active,
    they will wait in the queue until a thread is available.
  
  * If any thread terminates due to a failure during execution 
    prior to shutdown,a new one will take its place if needed to 
    execute remaining tasks.
 
  * The threads in the pool will exist until it is explicitly shutdown.
    
    To start the execution of Scheduled Thread pool we have to use following
    methods
    
    schedule(task,Intialdelay, Timeunit)
    - Submits a one-shot task that becomes enabled after the given delay.

    scheduleAtFixedRate(task, initialDelay, period, unit)
    
   - Submits a periodic action that becomes enabled first after the 
     given initial delay, and subsequently with the given period;

     The sequence of task executions continues indefinitely until 
     one of the following exceptional completions occur: 
      - The task is explicitly cancelled via the returned future. 
      - The executor terminates, also resulting in task cancellation. 
      - An execution of the task throws an exception. 
    
    
    Single thread executor
    * A Thread pool that uses a single worker thread operating off an unbounded queue. 
  
    * If this single thread terminates due to a failure during execution prior to shutdown,
      a new one will take its place if needed to execute remaining tasks.
      
    * Tasks are guaranteed to execute sequentially, and no more than one task will be active at 
      any given time. 
   
   
    RACE CONDITION
    
    - Multiple threads trying to access same Object at the same time
      is called as RACE CONDITION.
    - RACE CONDITION always leads to inconsistent data  
    
    - RACE CONDITION can be overcome by using Thread Synchronization
    
    Thread Synchronization
 
   - Thread Synchronization is executing threads in the sequential 
     order where one thread will execute only after other thread
     completes the execution.
     
   - Thread Synchronization can be achieved in 2 ways
     
     - using Synchronized methods
     - using Synchronized blocks
     
     * Synchronized methods
       - any method which is declared by using Synchronized keyword is called
         as Synchronized method.
       
       - If a thread calls the Synchronized method of the class then the thread
         will acquire the lock on the given object and other threads will not be 
         able to access the same object at the same time.
         
         Hence race condition is avoided.  
         
 
    * Synchronized blocks
    
     - Synchronized block will lock the given object until the thread
       completes its execution using the given object. This prevents
       other threads accessing the same object at the same time and
       hence race condition is avoided.
       
       syntax:
            synchronized (object_ref) 
			{
				stmt
				stmt
				stmt
			}
     - Synchronized blocks are used to perform thread safe operations
       on those objects whose class is not thread safe.
 
 
 
     Thread DeadLock
     - It is a situation where 2 threads are waiting to lock the objects
       of each other to complete the execution and wait for infinite period
       of time.
       
     * Thread DeadLock can be overcome by using Inter Thread Communication(ITC)  
       
       
       Inter Thread Communication(ITC) is achieved by using methods of Object class
       
       wait()
       notify()
       notifyAll()
       
     wait()      : It will pause the execution of the thread and also release all
                   the object locks held by the given thread.
       
     notify()    : It will send the notification to the thread which is in wait state
                   to resume its execution.
       
     notifyAll() : It will send the notification to all threads which are in wait state
                   to resume its execution.
