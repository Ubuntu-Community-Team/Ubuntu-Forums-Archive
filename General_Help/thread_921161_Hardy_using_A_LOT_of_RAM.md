---
title: "Hardy using A LOT of RAM"
date: 2008-09-15
forum: General Help
---

### Post by pikaia on 2008-09-15
Hey everyone.

I have a 2.2 GB Dual Core AMD64 and 2 GB of RAM.  I just wanted to see how much resources are used on this machine.  My mind was blown.  All I'm running is Opera and mrxvt and system Monitor right now.  I've turned off A LOT of processes.  Bluetooth, cron, anacron, klogd, atd and a few more I can't recall. I ran the sysv-rc and turned off a bunch of start up apps, but my GNOME ubuntu 64 is using 1.9 GB of RAM and 1.5 GB of swap, I have all but emerald turned off for desktop effects (just for window theme).  I've installed Ubuntu 

Why is it using so much?  How can I lower the RAM use?  My XP dual boot is using only around 200MB.

Any help would be great.  Thanks.

Edit:  I restarted X and RAM use was at 365MB, after starting Opera and System Monitor its now at over 600MB and climbing.  Do I have a memory leak?

---

### Post by wfp on 2008-09-16
Open a Terminal and run top. Just type top in the terminal so you can pinpoint the problem.

---

### Post by ryanhaigh on 2008-09-16
Using your ram is a generally a good thing and Linux makes use of as much as it can all the time, have a look at this for more info:
[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

That said your situation is obviously not normal system behaviour, there is no way should be putting anywhere near that amount of data into swap. Use top or the gnome system monitor (system>admin>system monitor) to find what process is causing this excessive memory usage.

---

### Post by pbpersson on 2008-09-16
OK.....I am a GUI sort of guy.....I really don't do terminal stuff.

However, I tried this top thing just for the heck of it.

The GUI system monitor says my system is using 2.2GB of RAM....but the top thing says my system is using 3.8GB of RAM.

Someone is lying to me....  :(

---

### Post by crazypenguin2008 on 2008-09-16
im using a cobbled together 32bit system and here is my paste from the top command. ive noticed that hardy has been slowing recently....does anyone see anything out of the normal here?? i get two different figures from my system monitor and top also 

cummins12valve@cummins12valve-desktop:~$ top

top - 02:20:41 up  6:45,  2 users,  load average: 0.24, 0.48, 0.45
Tasks: 108 total,   1 running, 107 sleeping,   0 stopped,   0 zombie
Cpu(s): 15.2%us,  2.0%sy,  0.0%ni, 82.8%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    645280k total,   610596k used,    34684k free,    20356k buffers
Swap:   859436k total,    39780k used,   819656k free,   230212k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 4996 root      20   0  143m  44m 9.8m S  9.9  7.1  52:58.37 Xorg               
 8022 cummins1  20   0 74368  20m  11m S  6.0  3.3   0:07.06 gnome-terminal     
 5346 cummins1  20   0 13712 4796 3764 S  2.0  0.7   5:26.10 at-spi-registry    
 6548 root      20   0 37424  15m 9260 S  2.0  2.5   4:11.30 firestarter        
 5461 cummins1  20   0 23496  15m 5676 S  1.3  2.5   4:21.31 compiz.real        
    6 root      15  -5     0    0    0 S  0.7  0.0   0:06.18 events/0           
 4801 root      20   0  3416 1152 1004 S  0.7  0.2   0:24.76 hald-addon-inpu    
 4841 root      20   0  3420 1140  988 S  0.7  0.2   0:06.06 hald-addon-stor    
 5389 cummins1  20   0 17000 6508 5040 S  0.7  1.0   1:39.42 gnome-screensav    
 8042 cummins1  20   0  2304 1104  852 R  0.7  0.2   0:01.28 top                
 5359 cummins1  20   0 64712  34m 9528 S  0.3  5.5   0:26.02 gnome-settings-    
 5484 cummins1  20   0 23812  11m 8232 S  0.3  1.8   1:10.73 nm-applet          
 7313 cummins1  20   0  240m 107m  28m S  0.3 17.0  11:39.51 firefox            
    1 root      20   0  2844 1688  544 S  0.0  0.3   0:03.40 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 ksoftirqd/0

---

### Post by p_quarles on 2008-09-16
Okay, stop the madness! Before we can even call this a problem, we need to see the output of this command:
```
free -m
```
Please paste the results here.

---

### Post by crazypenguin2008 on 2008-09-16
```
cummins12valve@cummins12valve-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           630        611         18          0         22        228
-/+ buffers/cache:        360        269
Swap:          839         38        800
cummins12valve@cummins12valve-desktop:~$
```

---

### Post by p_quarles on 2008-09-16
> **crazypenguin2008 said:**
> ```
cummins12valve@cummins12valve-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           630        611         18          0         22        228
-/+ buffers/cache:        360        269
Swap:          839         38        800
cummins12valve@cummins12valve-desktop:~$
```
No, that's perfectly normal and healthy memory usage.

---

### Post by crazypenguin2008 on 2008-09-16
thanks for teh reasurance

---

