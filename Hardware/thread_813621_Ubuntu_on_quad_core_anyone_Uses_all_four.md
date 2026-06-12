---
title: "Ubuntu on quad core anyone? Uses all four?"
date: 2008-05-31
forum: Hardware
---

### Post by ingrid_ozikem on 2008-05-31
I was trying to decide between two CPUs in the same price range,
 
Intel Core 2 Quad Q6600 2.4GHz  1066MHz FSB

and

Intel Core 2 Duo E8400 3.0GHz  1333MHz FSB

This is a common question discussed all over in the Windows context -- if your programs/OS can't use 4 cores well, the faster double core is better. 


Questions is, where is Ubuntu on this? Does anyone here have it running on the Intel Q6600? If you have many many applications open, does it run them on different cores? I'm more interested in that (many many 'small' applications) than in one large application..


Answers would be very helpful! I asked a related question in the Absolute Baby forum and got some useful responses (more related to AMD and whether Ubuntu works at all) but I am particularly interested in performance -- does it work well?  I'm trying to build a machine that I can make the BEST use of using Ubuntu and don't want to later find out that only Vista works with my specs..

---

### Post by tamoneya on 2008-05-31
I have a Q6600 running at 3.10GHz+.  Here is the output of top:```
tamoneya@ubuntu0:~/Desktop$ top

top - 00:27:42 up  3:32,  3 users,  load average: 2.90, 3.26, 3.01
Tasks: 149 total,   1 running, 148 sleeping,   0 stopped,   0 zombie
Cpu(s):  3.5%us,  3.7%sy, 48.3%ni, 44.0%id,  0.0%wa,  0.0%hi,  0.5%si,  0.
Mem:   4036600k total,  3623568k used,   413032k free,    21064k buffers
Swap: 11823800k total,    43104k used, 11780696k free,  2631856k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND      
11937 tamoneya  39  19  188m 137m 1876 S   95  3.5  26:20.70 FahCore_a1.ex
11938 tamoneya  39  19  142m  93m 1680 S   56  2.4  14:24.32 FahCore_a1.ex
11939 tamoneya  39  19  141m  92m 1680 S   36  2.3   9:34.70 FahCore_a1.ex
11940 tamoneya  39  19  140m  90m 1692 S   28  2.3   6:53.95 FahCore_a1.ex
 8516 root      20   0  979m  94m  11m S    3  2.4   5:59.41 Xorg         
 9105 tamoneya  20   0  136m 7024 4656 S    2  0.2   0:10.60 gnome-screens
 9112 tamoneya  20   0  313m  28m  14m S    1  0.7   0:15.52 gnome-panel  
 9177 tamoneya  20   0  275m  35m  12m S    1  0.9   0:01.56 gnome-termina
 9113 tamoneya  20   0  509m  46m  16m S    0  1.2   0:15.28 nautilus     
 9171 tamoneya  20   0  294m  38m  13m S    0  1.0   0:51.74 compiz.real  
11129 tamoneya  20   0  639m  40m  20m S    0  1.0   0:06.90 pidgin       
    1 root      20   0  4016  888  600 S    0  0.0   0:00.84 init         
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd     
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0  
    4 root      15  -5     0    0    0 S    0  0.0   0:00.30 ksoftirqd/0  
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0   
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1  
    7 root      15  -5     0    0    0 S    0  0.0   0:00.02 ksoftirqd/1  
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1   
    9 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/2  
   10 root      15  -5     0    0    0 S    0  0.0   0:00.02 ksoftirqd/2  
   11 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/2   
   12 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/3  
   13 root      15  -5     0    0    0 S    0  0.0   0:00.02 ksoftirqd/3  
   14 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/3   
   15 root      15  -5     0    0    0 S    0  0.0   0:00.10 events/0     
   16 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/1     
   17 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/2     
   18 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/3     
   19 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper      
   55 root      15  -5     0    0    0 S    0  0.0   0:00.20 kblockd/0    
   56 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1    
   57 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/2    
   58 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/3    
   61 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid       
   62 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify 
  150 root      15  -5     0    0    0 S    0  0.0   0:00.00 kseriod      
  207 root      20   0     0    0    0 S    0  0.0   0:00.52 pdflush      
  208 root      20   0     0    0    0 S    0  0.0   0:20.98 pdflush 
```I run F@H on my comptuer and it still runs like butter.  I would highly recommend the quad core.

---

### Post by hotweiss on 2008-05-31
> **ingrid_ozikem said:**
> I was trying to decide between two CPUs in the same price range,
 
Intel Core 2 Quad Q6600 2.4GHz  1066MHz FSB

and

Intel Core 2 Duo E8400 3.0GHz  1333MHz FSB

This is a common question discussed all over in the Windows context -- if your programs/OS can't use 4 cores well, the faster double core is better. 


Questions is, where is Ubuntu on this? Does anyone here have it running on the Intel Q6600? If you have many many applications open, does it run them on different cores? I'm more interested in that (many many 'small' applications) than in one large application..


Answers would be very helpful! I asked a related question in the Absolute Baby forum and got some useful responses (more related to AMD and whether Ubuntu works at all) but I am particularly interested in performance -- does it work well?  I'm trying to build a machine that I can make the BEST use of using Ubuntu and don't want to later find out that only Vista works with my specs..

I also had that same problem, and I came to the conlcusion that it is better to get a faster dual core. In most situations you will only be using one core anyways... Quadcore's only pay off if you do number crunching, video conversion, etc...

---

### Post by ingrid_ozikem on 2008-05-31
Thanks to both of you!! I really wish people discussed this issue more for Ubuntu.. googling E8400 vs Q6600 , you'll find 100s of discussions related to Windows. (Or does the OS not matter?)

I'm leaning towards the Q6600 Quad Core but:

Tamoneya: Is F@H programmed to run on 4 cores or is Ubuntu splitting it up somehow? Or do you have 4 instances running? (I'll be using Mathematica..) And those CPU%s are for individual cores even though the CPU is not identified on each line?

Hotweiss (and anyone else):

 What I really want to do is mostly run and have open many many applications.. each of them in itself a small application (like PDF viewers, browsers, Latex compiler, Mathematica (the most intensive thing I'll run), music players... you get the idea.)

 If I run such a long list of apps, will they automatically run on different cores? If so, isn't the quad core obviously a better choice? Even if you don't have applications that know how to break up into threads?

 Or do small single apps not get distributed to several cores so easily by Ubuntu?

---

### Post by chewearn on 2008-05-31
> **ingrid_ozikem said:**
> Thanks to both of you!! I really wish people discussed this issue more for Ubuntu.. googling E8400 vs Q6600 , you'll find 100s of discussions related to Windows. (Or does the OS not matter?)


For normal usage, it doesn't matter.  Computer hardware has leaped far ahead of software nowadays.  Heck, people still run 32bit OS on 64bit CPU years after 64bit CPU came out.  Fact is, you barely use the power available in your hardware as it is.  Exceptions are those running e.g. intensive mathematical programs, software compiling, and latest 3D games.


> 
I'm leaning towards the Q6600 Quad Core but:

Tamoneya: Is F@H programmed to run on 4 cores or is Ubuntu splitting it up somehow? Or do you have 4 instances running? (I'll be using Mathematica..) And those CPU%s are for individual cores even though the CPU is not identified on each line?Since Tamoneya is offline, I will venture an answer.

F@H SMP version (there are a few versions) are multi-core aware.  That means, it's able to split the processes into each core and consume *all* spare CPU cycles.

In other words, you run F@H SMP once, and the programs split itself into four parts (if you have 4 cores), each part running in each core.

(In the past, this is not possible, and you have to run one F@H instance for each core you have, manually).


> 
Hotweiss (and anyone else):

 What I really want to do is mostly run and have open many many applications.. each of them in itself a small application (like PDF viewers, browsers, Latex compiler, Mathematica (the most intensive thing I'll run), music players... you get the idea.)

 If I run such a long list of apps, will they automatically run on different cores? If so, isn't the quad core obviously a better choice? Even if you don't have applications that know how to break up into threads?

 Or do small single apps not get distributed to several cores so easily by Ubuntu?If a program are not SMP aware, it will not be able to run in more than one core at one instance in time.

But, the linux SMP kernel is able to allocate programs to different cores (load balancing).  It might even run a program in one core now, and later runs it in another core.  These are done transparently w.r.t. to the program.

As mentioned, you will probably not see a difference between 2 or 4 cores when runnning multiple programs.  Most of the time, the programs will do nothing (sleep), until the kernel wakes it up in respond to external input, a timer, etc.  So, most CPU cycles are wasted in idle loop anyways (unless you run something like F@H, which picks up the waste and put it to good use).

One last thing.  The two CPUs has different FSB.  In this regard, I might assume the one with higher FSB will be faster overall.

---

### Post by tamoneya on 2008-05-31
F@H has support for multicore processors.  I run it like this:```
./fah -smp
```Ubuntu will not be able to split a single core program onto four cores.  Processes dont work that way.  But since people almost always do some sort of multitasking it doesnt matter all that much since the tasks are automatically spread across the cores.

---

