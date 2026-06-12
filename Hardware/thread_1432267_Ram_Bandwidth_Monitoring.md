---
title: "Ram Bandwidth Monitoring"
date: 2010-03-17
forum: Hardware
---

### Post by medv4380 on 2010-03-17
I'm a programmer and I'm trying to build up my skill in Concurrency since now I have a quad core to work with.  I've run into a bit of a problem with a test app that is holding me back on some design choices.  My initial goal is to create a thread pool that will only ever utilize 3 of the 4 cores at 100%.  The first test went well since it was a thread pool of 3 threads and I tossed 4 near infinite processes into the pool and exactly 3 cores went to 100%.  The second test didn't go as well.  The second test is just a large number of short processes tossed into the thread pool.  The result seems to be one core at 100% and the other 2 to 3 floating between 10 - 50% yielding a process that runs at 200 - 250% in the process monitor.  I've looked into a number of possible causes, but I'm coming closer to believing that I may have a bandwidth bottleneck between my Ram and CPU.  Is there any way to monitor this so that I can confirm?  I am going to modify my test tonight to tray to utilize less ram but still have the same volume of processes sent to the thread pool.

Some things I've already checked but had no affect on CPU usage
[LIST]
[*]Used JNI to set Thread Affinity
[*]Increased Java Heap
[*]Used different Garbage Collector
[/LIST]

Just in case someone has incite outside of my question about monitoring the ram bandwidth here is my specs and code.

Specs 
CPU: AMD Phenom II X4 945 Deneb 3.0GHz 
RAM: 4GB 8-8-8-24 1600 DDR3 
Programming Language: Java 64bit 
OS: Ubuntu Linux 

Java
```

package test;
 
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
 
public class Main {
    public static int NumberOfThreads = 3; //Number of Cores being Tested
    public static int NumberOfRunners = 1000000; //Number of Runnable Operations
    public static int RunnerLoopLength = 10000; //Number of Interations for Each Runner
    public static int ThreadWaitLenghtInMS = 10000; //Lenths of time before the threadpool is Stopped.
    
    public static void main(String[] args) throws InterruptedException {
        ExecutorService pool = Executors.newFixedThreadPool(NumberOfThreads);
        Runner[] myRunner = new Runner[NumberOfRunners];
        System.out.println(myRunner.length);
        for(int ctr=0; ctr< myRunner.length; ctr++){
            myRunner[ctr] = new Runner();
        }
        for(Runner run:myRunner){
            pool.execute(run);
        }           
 
        Thread.sleep(ThreadWaitLenghtInMS);
 
        pool.shutdownNow();
 
        int failed = 0;
        for(int ctr=0; ctr< myRunner.length; ctr++){
            if(!myRunner[ctr].Ran)
                failed++;
        }
        System.out.println( "Failed: " + failed);
    }
 
    static class Runner implements Runnable {
        public boolean Ran = false;
        public void run() {
            Ran = true;
            for(int ctr=0; ctr<RunnerLoopLength; ctr++){
                double val = Math.PI;
            }
        }
    }
}

```

---

