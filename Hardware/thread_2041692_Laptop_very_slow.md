---
title: "Laptop very slow"
date: 2012-08-13
forum: Hardware
---

### Post by Nikolazigic on 2012-08-13
I do not know how to check where the problem is,just I have noticed it is getting slower and slower.
milenko@milenkons:~$ egrep  'GHz|MHz' /proc/cpuinfo
model name    : Pentium(R) Dual-Core CPU       T4200  @ 2.00GHz
cpu MHz        : 1200.000
model name    : Pentium(R) Dual-Core CPU       T4200  @ 2.00GHz
cpu MHz        : 1200.000
What should I do?
I have numerical computations,so It is better when it works properly.

---

### Post by hakermania on 2012-08-13
Hello Nikolazigic, if the system is getting slower and slower in a noticeable way, then I guess that there is a memory leak in an application you use?

Please use the **top** command to see what processes are running etc that may cause this.

---

### Post by Nikolazigic on 2012-08-13
Thanks,I have used top but do not know how to interpret this
milenko@milenkons:~$ top

top - 10:43:31 up  1:09,  3 users,  load average: 0.56, 0.85, 1.02
Tasks: 166 total,   1 running, 165 sleeping,   0 stopped,   0 zombie
Cpu(s):  3.6%us,  2.1%sy,  0.0%ni, 94.1%id,  0.0%wa,  0.1%hi,  0.0%si,  0.0%st
Mem:   2056112k total,  1758180k used,   297932k free,    62412k buffers
Swap:  6022136k total,      280k used,  6021856k free,   978356k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                             
 1696 milenko   20   0  385m 168m  21m S    3  8.4   4:15.49 plugin-containe                                                                                                     
 1038 root      20   0 60496  30m  11m S    3  1.5   4:44.66 Xorg                                                                                                                
 1927 milenko   20   0  123m  15m  11m S    2  0.8   0:06.32 gnome-terminal                                                                                                      
 1628 milenko   20   0  637m 179m  35m S    2  8.9   5:23.42 firefox                                                                                                             
 1345 milenko   20   0 71264  24m 7844 S    1  1.2   0:19.00 compiz                                                                                                              
   66 root      20   0     0    0    0 S    0  0.0   0:02.21 kondemand/1                                                                                                         
 1459 root      20   0  5184  876  608 S    0  0.0   0:00.74 udisks-daemon                                                                                                       
 3017 milenko   20   0  2544 1244  932 R    0  0.1   0:00.46 top

---

### Post by hakermania on 2012-08-13
Hm, I cannot figure out many things from your output, so let's go GUI way.

Please open the System Monitor program and go to Processes tab and make them sort by Memory usage (click on the Memory heading). Do you see any process eating a lot of RAM?

---

### Post by Nikolazigic on 2012-08-13
Yes,firefox for example do not know why.I am giving a scrrenchot.

---

### Post by Nikolazigic on 2012-08-13
so this firefox is somehow confusing.

---

### Post by hakermania on 2012-08-13
Both plugin-container and firefox are eating too much memory (plugin-container is run by firefox)

As I can see, you have too many instances of Firefox running. Of course, as you understand, it is no possible for any PC to run infinite instances of a process. The memory will be full and then the PC will lag. Why don't you try to have less concurrent instances running?

Also, as I can see, you are running MATLAB, thus the numerical computations you talked about earlier. Note that when you already do something resource consuming like numerical computations, don't too many things concurrently, you had better close other applications that may consume many resources as well.

So, the problem is not with the PC or the system, it is logical that, with so many processes running, the PC is turning to be slow. Close some processes!

---

