---
title: "X and L ubuntu on IBM X30 to slow"
date: 2012-08-07
forum: Hardware
---

### Post by komarx6 on 2012-08-07
I tried to install Xubuntu on my old IBM ThinkPad X30 (1GHz CPU, 384MB RAM, 20GB HDD).I succeeded using alternate usb install. But result was very bad. It's so slow that it hurts. I installed updates and reseted, but still to slow.
I tried Lubuntu too, but same thing. It was not RAM. Task Manager shows  (both on Xubuntu and Lubuntu) that there is plenty of RAM available. But  as soon as I try to open some program, CPU usage jumps to 100% and it  takes eternity to open it. And in the case of Xubuntu, CPU run at 100%  at least 50% of the time.
And when I turn computer on, I can't see anything until login screen...except loading screen for part of second when it flashes.
I know that these two systems are built for even older and slower  computers, but could it be that these systems are not comfortable with  this processor. Is there any cure for it. I would really like to install  some *ubuntu on it. Now I'll try to install Crunchbang to see how it would behave.

---

### Post by komarx6 on 2012-08-07
This is some information on cpu:
```
  *-cpu                   
       description: CPU
       product: Mobile Intel(R) Pentium(R) III CPU - M  1066MHz
       vendor: Intel Corp.
       physical id: 6
       bus info: cpu@0
       version: 6.11.4
       slot: None
       size: 731MHz
       capacity: 1066MHz
       width: 32 bits
       clock: 133MHz
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 mtrr pge mca cmov pse36 mmx fxsr sse up cpufreq
```

*I had to install gnome-terminal because I can't copy text from XTerm and LXTerminal.^C appears if using keyboard and using mouse makes no effect.*
this is result of "top":
```
top - 22:05:17 up 59 min,  2 users,  load average: 3.32, 2.69, 1.61
Tasks: 114 total,   1 running, 112 sleeping,   0 stopped,   1 zombie
Cpu(s): 34.2%us,  8.1%sy,  0.0%ni, 57.3%id,  0.3%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    369664k total,   340052k used,    29612k free,    11972k buffers
Swap:   572412k total,    19312k used,   553100k free,   143140k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 2300 marko     20   0  248m  67m  18m S 24.4 18.8   2:32.25 chromium-browse    
 1066 root      20   0 47652 9644 5032 S  8.2  2.6   2:35.44 Xorg               
 2591 marko     20   0  187m  14m  10m S  7.2  3.9   0:05.89 gnome-terminal     
 1600 marko     20   0  453m  45m  22m S  2.3 12.5   2:12.09 chromium-browse    
 2665 root      20   0  2824 1084  832 R  1.0  0.3   0:00.39 top                
 1416 marko     20   0  245m  12m 8528 S  0.3  3.4   0:02.94 nm-applet          
 1457 marko     20   0 20460 1896 1528 S  0.3  0.5   0:00.45 gvfs-afc-volume    
 1773 ntp       20   0  5728 1472 1020 S  0.3  0.4   0:00.46 ntpd               
    1 root      20   0  3516 1596 1028 S  0.0  0.4   0:01.09 init               
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      20   0     0    0    0 S  0.0  0.0   0:00.40 ksoftirqd/0        
    5 root      20   0     0    0    0 S  0.0  0.0   0:01.03 kworker/u:0        
    6 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    7 root      RT   0     0    0    0 S  0.0  0.0   0:00.04 watchdog/0         
    8 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 cpuset             

```

---

### Post by steeldriver on 2012-08-07
For the record, this is what I see on my X30, also running Xubuntu 12.04 (although I have the max 1G RAM)

```
steeldriver@lap-x30:~$ lshw -C cpu
WARNING: you should run this program as super-user.
  *-cpu                   
       product: Mobile Intel(R) Pentium(R) III CPU - M  1200MHz
       vendor: Intel Corp.
       physical id: 2
       bus info: cpu@0
       version: 6.11.4
       size: 1197MHz
       capacity: 1197MHz
       width: 32 bits
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 mtrr pge mca cmov pse36 mmx fxsr sse up cpufreq
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
steeldriver@lap-x30:~$ 
steeldriver@lap-x30:~$ top

top - 17:03:12 up 1 day,  4:01,  0 users,  load average: 0.94, 0.71, 0.51
Tasks: 144 total,   1 running, 142 sleeping,   0 stopped,   1 zombie
Cpu(s):  3.6%us,  2.6%sy,  0.0%ni, 93.8%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1017004k total,   863644k used,   153360k free,    93156k buffers
Swap:  1998844k total,     7916k used,  1990928k free,   398988k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1107 root      20   0 50268  15m 7652 S  1.7  1.5  20:24.38 Xorg               
 1567 steeldri   20   0  580m 183m  26m S  1.7 18.5  73:23.01 firefox            
 2497 steeldri   20   0  158m  35m  16m S  1.3  3.6  39:18.79 plugin-containe    
 4906 steeldri  20   0  2832 1108  832 R  0.7  0.1   0:00.08 top                
 4744 steeldri   20   0 53460  12m 9732 S  0.3  1.2   0:00.43 xfce4-terminal     
    1 root      20   0  3640 1864 1192 S  0.0  0.2   0:01.26 init               
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.02 kthreadd           
    3 root      20   0     0    0    0 S  0.0  0.0   0:04.79 ksoftirqd/0        
    6 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    7 root      RT   0     0    0    0 S  0.0  0.0   0:01.35 watchdog/0         
    8 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 cpuset             
    9 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 khelper            
   10 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kdevtmpfs          
   11 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 netns              
   12 root      20   0     0    0    0 S  0.0  0.0   0:00.32 sync_supers        
   13 root      20   0     0    0    0 S  0.0  0.0   0:00.00 bdi-default        
   14 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 kintegrityd        

```

---

