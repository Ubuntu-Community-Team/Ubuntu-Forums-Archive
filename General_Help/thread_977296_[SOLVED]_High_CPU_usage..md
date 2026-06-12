---
title: "[SOLVED] High CPU usage."
date: 2008-11-10
forum: General Help
---

### Post by johanhartman on 2008-11-10
Morning all,

Before with 8.04 system monitor showed my cpu usage to be at about 15% or so on average, with 8.10 though it never shows below 50%... Why?

PS: I have a Toshiba Satellite L40/17U (that is, Intel Pentium Dual CPU (T2330) at 1.6GHz each).

---

### Post by Ryadt on 2008-11-10
Can you post the output of ```
top
```

---

### Post by johanhartman on 2008-11-10
hehe, just as I finished posting the thread I though of supplying that, anyway, here it is:
```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                          
 5503 root      20   0  428m  89m 8956 R   15  9.0  10:18.53 Xorg                             
 4727 root      20   0  2968 1836  536 S    7  0.2   8:52.34 acpid                            
18667 johanhar  20   0 84068  24m  12m S    5  2.4   0:01.42 gnome-terminal                   
 1183 johanhar  20   0  271m 147m  26m S    3 14.8  10:05.22 firefox                          
 5369 haldaemo  20   0  2296  944  804 S    2  0.1   2:07.48 hald-addon-acpi                  
 5274 haldaemo  20   0  6400 4360 3592 S    2  0.4   2:26.63 hald                             
27836 johanhar  20   0 23052  15m 7100 S    1  1.5   0:34.62 compiz.real                      
    4 root      15  -5     0    0    0 S    1  0.0   0:22.66 ksoftirqd/0                      
 2481 johanhar  20   0  2416 1168  884 R    1  0.1   0:00.08 top                              
23913 johanhar  20   0 39768  22m  13m S    1  2.3   0:12.96 gnome-panel                      
26645 johanhar  20   0 21252 3212 1848 S    1  0.3   0:17.12 gnome-screensav                  
31471 johanhar  20   0 24464  11m 8684 S    1  1.2   0:35.60 multiload-apple                  
    1 root      20   0  3056 1884  564 S    0  0.2   0:02.54 init                             
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                         
    3 root      RT  -5     0    0    0 S    0  0.0   0:02.64 migration/0                      
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                       
    6 root      RT  -5     0    0    0 S    0  0.0   0:02.36 migration/1                      
    7 root      15  -5     0    0    0 S    0  0.0   0:23.34 ksoftirqd/1                      
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                       
    9 root      15  -5     0    0    0 S    0  0.0   0:00.10 events/0                         
   10 root      15  -5     0    0    0 S    0  0.0   0:04.38 events/1                         
   11 root      15  -5     0    0    0 S    0  0.0   0:04.30 khelper                          
   51 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/0                    
   52 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/1                    
   54 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0                        
   55 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1                        
   57 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid                           
   58 root      15  -5     0    0    0 S    0  0.0   0:05.40 kacpi_notify                     
  140 root      15  -5     0    0    0 S    0  0.0   0:00.00 cqueue                           
  144 root      15  -5     0    0    0 S    0  0.0   0:00.02 kseriod                          
  189 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush                          
  191 root      15  -5     0    0    0 S    0  0.0   0:00.06 kswapd0                          
  233 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0                            

```

---

### Post by Ryadt on 2008-11-10
Your cpu usage seems to be ok. The only thing is that firefox seems to be using a lot of memory.

---

### Post by johanhartman on 2008-11-10
I can handle that, although if you can point to a site or post that will help get that down it'll be most appreciated. Its just bothering me slightly that the cpus are running at 50% when the system is idle

---

### Post by carlmig on 2008-11-10
I'm also noticing high cpu usage, but I could trace down the problem a little further. 
I was noticing that my system only got slower after a while, not right from the beginning when I logged in. Eventually I could trace down to Nautilus. If I don't open Nautilus, my system runs fine. Right after opening Nautilus my system becomes incredibly slow, and stays that way even after killing nautilus. And the strange part is that, the process that has high cpu is not nautilus itself, but Xorg.
The test I use is pressing some letter key (for a while) in a text editor. Ideally it should print the letters smoothly and fast. After loading Nautilus, it prints some, it hangs, print some more, hangs again, etc...cpu is at 100% when I do that.
For now, the only way I could find to fix this is to logoff and log in back again. Killing nautilus doesn't fix it...as I said it's the xorg process that has high cpu.

Any ideas ?

Thanks

---

### Post by johanhartman on 2008-11-10
> **carlmig said:**
> I'm also noticing high cpu usage, but I could trace down the problem a little further. 
I was noticing that my system only got slower after a while, not right from the beginning when I logged in. Eventually I could trace down to Nautilus. If I don't open Nautilus, my system runs fine. Right after opening Nautilus my system becomes incredibly slow, and stays that way even after killing nautilus. And the strange part is that, the process that has high cpu is not nautilus itself, but Xorg.
The test I use is pressing some letter key (for a while) in a text editor. Ideally it should print the letters smoothly and fast. After loading Nautilus, it prints some, it hangs, print some more, hangs again, etc...cpu is at 100% when I do that.
For now, the only way I could find to fix this is to logoff and log in back again. Killing nautilus doesn't fix it...as I said it's the xorg process that has high cpu.

Any ideas ?

Thanks

After doing the text editor text as described by you it seems our problems are not similar. What are your performance specs, maybe my cpu can handle the extra load a little better.

I haven't really noticed any major performance loss since the update, mainly because I don't use very demanding software. But still it can't be good for battery life can it?

---

### Post by carlmig on 2008-11-10
> **johanhartman said:**
> After doing the text editor text as described by you it seems our problems are not similar. What are your performance specs, maybe my cpu can handle the extra load a little better.

I haven't really noticed any major performance loss since the update, mainly because I don't use very demanding software. But still it can't be good for battery life can it?

I don't believe my CPU will make that difference. It's a T9400 @ 2.5Ghz

---

### Post by spibou on 2008-11-10
> **johanhartman said:**
> hehe, just as I finished posting the thread I though of supplying that, anyway, here it is:
```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                          
 5503 root      20   0  428m  89m 8956 R   15  9.0  10:18.53 Xorg                             
 4727 root      20   0  2968 1836  536 S    7  0.2   8:52.34 acpid                            
18667 johanhar  20   0 84068  24m  12m S    5  2.4   0:01.42 gnome-terminal                   
 1183 johanhar  20   0  271m 147m  26m S    3 14.8  10:05.22 firefox                          
 5369 haldaemo  20   0  2296  944  804 S    2  0.1   2:07.48 hald-addon-acpi                  
 5274 haldaemo  20   0  6400 4360 3592 S    2  0.4   2:26.63 hald                             
27836 johanhar  20   0 23052  15m 7100 S    1  1.5   0:34.62 compiz.real                      
    4 root      15  -5     0    0    0 S    1  0.0   0:22.66 ksoftirqd/0                      
 2481 johanhar  20   0  2416 1168  884 R    1  0.1   0:00.08 top                              
23913 johanhar  20   0 39768  22m  13m S    1  2.3   0:12.96 gnome-panel                      
26645 johanhar  20   0 21252 3212 1848 S    1  0.3   0:17.12 gnome-screensav                  
31471 johanhar  20   0 24464  11m 8684 S    1  1.2   0:35.60 multiload-apple                  
    1 root      20   0  3056 1884  564 S    0  0.2   0:02.54 init                             
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                         
    3 root      RT  -5     0    0    0 S    0  0.0   0:02.64 migration/0                      
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                       
    6 root      RT  -5     0    0    0 S    0  0.0   0:02.36 migration/1                      
    7 root      15  -5     0    0    0 S    0  0.0   0:23.34 ksoftirqd/1                      
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                       
    9 root      15  -5     0    0    0 S    0  0.0   0:00.10 events/0                         
   10 root      15  -5     0    0    0 S    0  0.0   0:04.38 events/1                         
   11 root      15  -5     0    0    0 S    0  0.0   0:04.30 khelper                          
   51 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/0                    
   52 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/1                    
   54 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0                        
   55 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1                        
   57 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid                           
   58 root      15  -5     0    0    0 S    0  0.0   0:05.40 kacpi_notify                     
  140 root      15  -5     0    0    0 S    0  0.0   0:00.00 cqueue                           
  144 root      15  -5     0    0    0 S    0  0.0   0:00.02 kseriod                          
  189 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush                          
  191 root      15  -5     0    0    0 S    0  0.0   0:00.06 kswapd0                          
  233 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0                            

```
I find it puzzling that a sleeping gnome-terminal uses 5% of CPU time. Did you have any application output to gnome-terminal at the time? If it was top itself then it's still puzzling. Even if I have top running on top of gnome-terminal and updating the screen every second, gnome-terminal uses 0% of CPU time. Compared to my experience, Xorg also uses a lot.

---

### Post by Crio on 2008-11-11
I have this issue too. My machine is Toshiba Satellite L40-14G (1.7GHz Celeron). I've just installed Ubuntu 8.10 and, according to monitor, CPU is maxed out constantly. Desktop does not feel jerky though, typing is fine, and fans does not go into overdrive, so, I wonder, can it be an error in reporting? Anyway, it bothers me, because it is certainly not normal.  
top (see below) shows that most of the CPU usage is due to the system, but unfortunately I've no idea how to investigate further. Any suggestions? 

```
top - 10:01:22 up  1:34,  3 users,  load average: 2.79, 3.02, 2.98
Tasks: 129 total,   5 running, 124 sleeping,   0 stopped,   0 zombie
Cpu(s): 38.2%us, 61.1%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.7%hi,  0.0%si,  0.0%st
Mem:   1025084k total,   929332k used,    95752k free,    35988k buffers
Swap:  2433808k total,     1792k used,  2432016k free,   387532k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5126 root      20   0  458m 117m  10m S 12.3 11.7   9:21.40 Xorg               
 4551 root      20   0  2836 1768  536 S  6.3  0.2   5:50.88 acpid              
26454 root      20   0 58524  46m  22m S  3.3  4.6   3:20.95 synaptic           
 4972 gombo     20   0 26184  18m 7200 S  2.0  1.8   0:57.03 compiz.real        
 4878 haldaemo  20   0  6440 4428 3616 S  1.7  0.4   1:43.19 hald               
 4977 haldaemo  20   0  2296  940  804 S  1.7  0.1   1:48.80 hald-addon-acpi    
 5453 gombo     20   0 98.6m  24m  12m R  1.3  2.5   0:01.34 gnome-terminal     
18286 gombo     20   0  176m  86m  22m S  1.3  8.7   2:57.31 firefox            
   51 root      15  -5     0    0    0 S  0.7  0.0   0:07.74 kacpi_notify       
 7648 gombo     20   0 21492  12m 7480 S  0.7  1.2   0:09.64 gtk-window-deco    
14900 gombo     20   0 41816  25m  13m S  0.7  2.6   0:12.54 gnome-panel        
32374 gombo     20   0 24948  14m 8220 S  0.7  1.4   0:01.22 notification-da    
    1 root      20   0  3056 1888  564 S  0.0  0.2   0:01.36 init               

```

---

### Post by johanhartman on 2008-11-11
> **carlmig said:**
> I don't believe my CPU will make that difference. It's a T9400 @ 2.5Ghz

Hehe, yeah somehow I don't think so either:D, just a suggestion...

---

### Post by johanhartman on 2008-11-11
> **spibou said:**
> I find it puzzling that a sleeping gnome-terminal uses 5% of CPU time. Did you have any application output to gnome-terminal at the time? If it was top itself then it's still puzzling. Even if I have top running on top of gnome-terminal and updating the screen every second, gnome-terminal uses 0% of CPU time. Compared to my experience, Xorg also uses a lot.

I can't remember if I had anything running at the time so for the sake of elimination I did another one,this time I made sure that the only application running (in the foreground anyway) was gnome terminal (to do the test). Here are the results:

```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 4728 root      20   0  2968 1836  536 R    8  0.2   2:36.80 acpid              
 5515 root      20   0  403m  68m 8768 S    3  6.8   3:22.50 Xorg               
 5285 haldaemo  20   0  6464 4432 3592 S    2  0.4   0:44.08 hald               
 5380 haldaemo  20   0  2296  944  804 S    1  0.1   0:37.62 hald-addon-acpi    
  310 johanhar  20   0 19972  11m 5916 S    1  1.2   0:17.74 compiz.real        
16432 johanhar  20   0  135m  32m  14m S    1  3.2   0:02.02 gnome-terminal     
    1 root      20   0  3056 1884  564 S    0  0.2   0:02.54 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.78 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:06.74 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.72 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:06.90 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.02 khelper            

```

I did not pay attention with Hardy but is ACPID supposed to take up that much resources. What I dont understand is that if you look at these results then the cpu should be running at around 16%, which I would consider normal, yet system monitor insists its around 55%. Maybe this is just a system monitor bug.

---

### Post by johanhartman on 2008-11-11
> **Crio said:**
> I have this issue too. My machine is Toshiba Satellite L40-14G (1.7GHz Celeron). I've just installed Ubuntu 8.10 and, according to monitor, CPU is maxed out constantly. Desktop does not feel jerky though, typing is fine, and fans does not go into overdrive, so, I wonder, can it be an error in reporting? Anyway, it bothers me, because it is certainly not normal.  
top (see below) shows that most of the CPU usage is due to the system, but unfortunately I've no idea how to investigate further. Any suggestions? 

```
top - 10:01:22 up  1:34,  3 users,  load average: 2.79, 3.02, 2.98
Tasks: 129 total,   5 running, 124 sleeping,   0 stopped,   0 zombie
Cpu(s): 38.2%us, 61.1%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.7%hi,  0.0%si,  0.0%st
Mem:   1025084k total,   929332k used,    95752k free,    35988k buffers
Swap:  2433808k total,     1792k used,  2432016k free,   387532k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5126 root      20   0  458m 117m  10m S 12.3 11.7   9:21.40 Xorg               
 4551 root      20   0  2836 1768  536 S  6.3  0.2   5:50.88 acpid              
26454 root      20   0 58524  46m  22m S  3.3  4.6   3:20.95 synaptic           
 4972 gombo     20   0 26184  18m 7200 S  2.0  1.8   0:57.03 compiz.real        
 4878 haldaemo  20   0  6440 4428 3616 S  1.7  0.4   1:43.19 hald               
 4977 haldaemo  20   0  2296  940  804 S  1.7  0.1   1:48.80 hald-addon-acpi    
 5453 gombo     20   0 98.6m  24m  12m R  1.3  2.5   0:01.34 gnome-terminal     
18286 gombo     20   0  176m  86m  22m S  1.3  8.7   2:57.31 firefox            
   51 root      15  -5     0    0    0 S  0.7  0.0   0:07.74 kacpi_notify       
 7648 gombo     20   0 21492  12m 7480 S  0.7  1.2   0:09.64 gtk-window-deco    
14900 gombo     20   0 41816  25m  13m S  0.7  2.6   0:12.54 gnome-panel        
32374 gombo     20   0 24948  14m 8220 S  0.7  1.4   0:01.22 notification-da    
    1 root      20   0  3056 1888  564 S  0.0  0.2   0:01.36 init               

```

Sorry for so many posts in succession. But if I look at your results then it also seems to suggest that your cpus are running at normal speed or at least its certainly not maxed out. So maybe as you suggest system monitor is at fault, unless I'm misunderstanding...

---

### Post by Ryadt on 2008-11-11
> **johanhartman said:**
> I can't remember if I had anything running at the time so for the sake of elimination I did another one,this time I made sure that the only application running (in the foreground anyway) was gnome terminal (to do the test). Here are the results:

```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 4728 root      20   0  2968 1836  536 R    8  0.2   2:36.80 acpid              
 5515 root      20   0  403m  68m 8768 S    3  6.8   3:22.50 Xorg               
 5285 haldaemo  20   0  6464 4432 3592 S    2  0.4   0:44.08 hald               
 5380 haldaemo  20   0  2296  944  804 S    1  0.1   0:37.62 hald-addon-acpi    
  310 johanhar  20   0 19972  11m 5916 S    1  1.2   0:17.74 compiz.real        
16432 johanhar  20   0  135m  32m  14m S    1  3.2   0:02.02 gnome-terminal     
    1 root      20   0  3056 1884  564 S    0  0.2   0:02.54 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.78 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:06.74 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.72 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:06.90 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.02 khelper            

```

I did not pay attention with Hardy but is ACPID supposed to take up that much resources. What I dont understand is that if you look at these results then the cpu should be running at around 16%, which I would consider normal, yet system monitor insists its around 55%. Maybe this is just a system monitor bug.
It could be that the system monitor application is consuming the extra resources.

---

### Post by johanhartman on 2008-11-11
> **Ryadt said:**
> It could be that the system monitor application is consuming the extra resources.

Top with system monitor running:
```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
28577 johanhar  20   0 41008  21m  13m S    9  2.1   0:42.62 gnome-system-mo    
 4728 root      20   0  2968 1844  536 R    7  0.2   6:04.79 acpid              
 5515 root      20   0  430m  94m 9560 S    5  9.4   8:46.99 Xorg               
20092 haldaemo  20   0  6452 4112 3388 S    2  0.4   0:31.84 hald               
20864 haldaemo  20   0  2296  944  804 S    1  0.1   0:27.70 hald-addon-acpi    
    4 root      15  -5     0    0    0 S    1  0.0   0:15.42 ksoftirqd/0        
  310 johanhar  20   0 20104  12m 5924 S    1  1.2   0:38.40 compiz.real        
 4372 johanhar  20   0 24356  11m 8680 S    1  1.2   0:25.66 multiload-apple    
    1 root      20   0  3056 1884  564 S    0  0.2   0:02.56 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:01.82 migration/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:01.76 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:15.62 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.06 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.06 events/1           

```

As you can see its the top consumer. I'm wondering it doesn't show up like that normally since I have the system monitor applet on my top gnome-panel running all the time. Still not 55%.

---

### Post by Crio on 2008-11-11
System reports that the CPU (I have only one) is maxed out. Look at the line

Cpu(s): 38.2%us, 61.1%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.7%hi,  0.0%si,  0.0%st

User space usage 38.2% (and process more or less add up to this number), hardware interrupt 0.7% is fine, but where does system usage of 61.1% came from?

I wonder  what it reports in your case. If you do not see that line in the header of top you can toggle it on by pressing "t".

---

### Post by johanhartman on 2008-11-11
I see, I missed that bit, mine says;

Cpu(s): 18.4%us, 34.2%sy,  0.0%ni, 47.3%id,  0.0%wa,  0.2%hi,  0.0%si,  0.0%st

That makes a bit more sense then. Its a bit high though isn't it, also, any idea what the "id" parameter is for?

---

### Post by spibou on 2008-11-11
> **johanhartman said:**
> I see, I missed that bit, mine says;

Cpu(s): 18.4%us, 34.2%sy,  0.0%ni, 47.3%id,  0.0%wa,  0.2%hi,  0.0%si,  0.0%st

That makes a bit more sense then. Its a bit high though isn't it,
I don't have any experience with laptops but 34.2% kernel time (or 61.1% in Crio's case) does seem high. One thing that consumes a lot of kernel time is starting processes. So a suggestion to both of you is to think whether one of the programmes you have running is likely to constantly spawn (and then stop) child processes. There is also a slabtop utility but I don't know what "kernel slab cache" is.

> also, any idea what the "id" parameter is for?
Strange, the top man page doesn't mention it at all. But I will guess it's time spent idle.

Otherwise, the results [you posted](http://ubuntuforums.org/showpost.php?p=6150106&postcount=12) look normal with the possible exception of acpid but perhaps a hard working acpid is a laptop thing?

---

### Post by johanhartman on 2008-11-11
> **spibou said:**
> So a suggestion to both of you is to think whether one of the programmes you have running is likely to constantly spawn (and then stop) child processes.

Any idea where to start looking?

---

### Post by Link64x on 2008-11-11
Hey I'm having a very similar problem.  I'm very new to Linux (not new to Unix, but the Linux system... i have mac, which prolly doesn't count but w/e)... so i'm totally confused.  I was reading what people are saying, and actually it's pretty much the same as me... I have a laptop with Xubuntu 8.10 loaded onto it.  It has only 1Ghz, and 22G free hd space, but it ran very well prior to putting Linux on it.  However, it cannot seem to run anything past basic applications now without the CPU usage going to 100%.  For example, with only Terminal and System Manager open, System Manager reports between 32-43% CPU Usage.  It doesn't slow operation on the desktop down, but it does slow everything else down, except Firefox.  Also, upon opening even Terminal, CPU Usage spikes to 100%, it runs slow for about 10 seconds, then everything returns to normal.  Anything full-screen, such as the free FPS Nexuiz runs at about 2-4 frames per second.  Even the screen saver slows to a crawl.  Laptop btw is a Dell Inspiron 4100... my top results aren't worth my time to post (i'm posting from my mac because this laptop is have such trouble), reason being that it pretty much echos what everyone else has been saying.  Xorg is taking up 24%, gnome-system-monitor is taking up 15%, terminal and top take up .5% each, and that's really all that's worth mentioning.  Anyone got any suggestions?

~Nick~

---

### Post by spibou on 2008-11-11
> **johanhartman said:**
> Any idea where to start looking?
No but think back to your usage patterns. When did you first notice the problem? **ps -elf** tells you when each application was started. Study that and try to think if you're using any application out of the ordinary. Experiment with stopping non essential applications. Experiment with running the system just from console without Xorg running. It's a lot (and boring)  work and it may turn out that my guess is wrong but I can't think of any other answer.

Link64x, does your terminal use an image as background? It may be that you don't have enough memory and gnome-terminal (if that's what you're using) is memory hungry. Try using instead a more lightweight terminal emulator like xterm.

> **Link64x said:**
> my top results aren't worth my time to post (i'm posting from my mac because this laptop is have such trouble), reason being that it pretty much echos what everyone else has been saying.

I will suggest that you post them all the same. Someone might notice something. I read a few hours ago a different thread where someone had performance problems and from the output of top someone else noticed that the first poster was using 0 swap. What you *think* is relevant may not be relevant so it's best to post the data.

> Xorg is taking up 24%, gnome-system-monitor is taking up 15%, terminal and top take up .5% each, and that's really all that's worth mentioning.
Is that 0.5% or you made a typo?

---

### Post by Crio on 2008-11-12
Now, it is acpid after all.  I switched off acpid service and CPU usage imeddiately shrinked. Here is top output:

```
top - 09:52:00 up 11 min,  2 users,  load average: 0.13, 0.66, 0.62
Tasks: 115 total,   1 running, 114 sleeping,   0 stopped,   0 zombie
Cpu(s): 12.7%us,  1.3%sy,  0.0%ni, 85.7%id,  0.0%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:   1025084k total,   664020k used,   361064k free,    19200k buffers
Swap:  2433808k total,        0k used,  2433808k free,   258936k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5130 root      20   0  393m  48m 9184 S  8.0  4.8   0:36.66 Xorg               
12102 gombo     20   0  193m  74m  22m S  7.0  7.5   0:33.45 firefox            
16761 gombo     20   0 99.1m  24m  13m S  1.3  2.5   0:00.80 gnome-terminal     
26971 gombo     20   0 22568  14m 6032 S  1.3  1.4   0:04.50 compiz.real        
18472 gombo     20   0  8356 5312 2260 S  0.7  0.5   0:00.72 gconfd-2           
    1 root      20   0  3056 1888  564 S  0.0  0.2   0:01.36 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                

```

That's nice, but now what? Is it a bug or err... some kind of feature? :D
Should I file a bugreport?

P.S.: I've checked logs and all mentions of acpid goes like
```

Nov 12 09:44:42 gombo-laptop acpid: client connected from 5130[0:0] 
Nov 12 09:44:46 gombo-laptop acpid: client connected from 4981[111:122] 
Nov 12 09:45:26 gombo-laptop acpid: exiting 

```

---

### Post by johanhartman on 2008-11-12
> **Crio said:**
> Now, it is acpid after all.  I switched off acpid service and CPU usage imeddiately shrinked. Here is top output:

```
top - 09:52:00 up 11 min,  2 users,  load average: 0.13, 0.66, 0.62
Tasks: 115 total,   1 running, 114 sleeping,   0 stopped,   0 zombie
Cpu(s): 12.7%us,  1.3%sy,  0.0%ni, 85.7%id,  0.0%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:   1025084k total,   664020k used,   361064k free,    19200k buffers
Swap:  2433808k total,        0k used,  2433808k free,   258936k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5130 root      20   0  393m  48m 9184 S  8.0  4.8   0:36.66 Xorg               
12102 gombo     20   0  193m  74m  22m S  7.0  7.5   0:33.45 firefox            
16761 gombo     20   0 99.1m  24m  13m S  1.3  2.5   0:00.80 gnome-terminal     
26971 gombo     20   0 22568  14m 6032 S  1.3  1.4   0:04.50 compiz.real        
18472 gombo     20   0  8356 5312 2260 S  0.7  0.5   0:00.72 gconfd-2           
    1 root      20   0  3056 1888  564 S  0.0  0.2   0:01.36 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                

```

That's nice, but now what? Is it a bug or err... some kind of feature? :D
Should I file a bugreport?

P.S.: I've checked logs and all mentions of acpid goes like
```

Nov 12 09:44:42 gombo-laptop acpid: client connected from 5130[0:0] 
Nov 12 09:44:46 gombo-laptop acpid: client connected from 4981[111:122] 
Nov 12 09:45:26 gombo-laptop acpid: exiting 

```

NICE!, That looks a lot better, how did you stop acpid, just from system monitor?

---

### Post by spibou on 2008-11-12
> **Crio said:**
> Now, it is acpid after all.  I switched off acpid service and CPU usage imeddiately shrinked. 
<S N I P>
That's nice, but now what?
What I would do would be to restart acpid and use strace to see what it does. But tracing slows down processes so if acpid already uses up a lot of CPU time it is possible that when traced it will slow your system to crawl. Not likely but possible so before trying such an experiment save all your data so that even a hard reboot won't cause you to lose anything.

---

### Post by Link64x on 2008-11-12
[QUOTE="spibou"]I read a few hours ago a different thread where someone had performance problems and from the output of top someone else noticed that the first poster was using 0 swap. What you think is relevant may not be relevant so it's best to post the data.
[/QUOTE]

Rofl... actually, i'm not using any swap xD how do i change that?

[EDIT:] Actually, I have 1.2 GiB of swap, but i've never seen it used, that's all... so i'm assuming that's not it.  I'm going to post my top results in my next post, just gotta hook up the laptop to the internet...

~Nick~

---

### Post by Link64x on 2008-11-12
Ok, here's my results from top with only firefox and terminal running:

```
top - 21:40:45 up 13 min,  2 users,  load average: 0.10, 0.26, 0.26
Tasks: 102 total,   3 running,  99 sleeping,   0 stopped,   0 zombie
Cpu(s):  6.9%us,  1.9%sy,  0.0%ni, 90.8%id,  0.0%wa,  0.4%hi,  0.0%si,  0.0%st
Mem:   1033456k total,   295212k used,   738244k free,    11164k buffers
Swap:  1253028k total,        0k used,  1253028k free,   126456k cached

    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0        
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 events/0          
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 khelper           
   46 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0     
   48 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 kblockd/0         
   50 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid            
   51 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify      
  129 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cqueue            
  133 root      15  -5     0    0    0 S  0.0  0.0   0:00.32 kseriod           
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 ksoftirqd/0       
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0        
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 events/0          
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 khelper           
   46 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0     
   48 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 kblockd/0         
   50 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid            
   51 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify      
  129 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cqueue            
```
One thing I didn't notice before is the 90% id.  I actually had that setting accidentally turned off, idk why.  Seems like a problem to me.  lol, but what I want to know is what it means xD and how I get that % down.  Any ideas?

[EDIT:] Top is kinda inconsistent on Linux?  I have that snapshot above, and two very different ones later on... here they are:

```
top - 21:51:06 up 23 min,  2 users,  load average: 0.42, 0.55, 0.45
Tasks:  98 total,   3 running,  95 sleeping,   0 stopped,   0 zombie
Cpu(s): 11.3%us,  2.0%sy,  0.0%ni, 45.2%id, 41.5%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1033456k total,   487724k used,   545732k free,    27800k buffers
Swap:  1253028k total,        0k used,  1253028k free,   233204k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND           
 5841 nick      20   0  196m  73m  21m R  6.6  7.3   1:41.99 firefox           
 4715 root      20   0 81924  23m 7172 S  2.7  2.3   1:36.56 Xorg              
 1192 root      15  -5     0    0    0 S  0.7  0.0   0:00.46 scsi_eh_1         
 4666 root      20   0 14632 2504 2072 S  0.7  0.2   0:00.48 NetworkManager    
 5563 nick      20   0 94340  27m  12m R  0.7  2.7   0:05.82 xfce4-terminal    
 6411 nick      20   0  2412 1132  884 R  0.7  0.1   0:00.36 top               
    1 root      20   0  3056 1888  564 S  0.0  0.2   0:02.26 init              
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd          
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0       
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.06 ksoftirqd/0       
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0        
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 events/0          
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 khelper           
   46 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0     
   48 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 kblockd/0         
   50 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid            
   51 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify 


top - 21:49:18 up 22 min,  2 users,  load average: 0.53, 0.60, 0.46
Tasks:  98 total,   1 running,  97 sleeping,   0 stopped,   0 zombie
Cpu(s): 34.6%us,  6.3%sy,  0.0%ni, 42.9%id, 16.3%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1033456k total,   489628k used,   543828k free,    27648k buffers
Swap:  1253028k total,        0k used,  1253028k free,   235728k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND           
 5841 nick      20   0  171m  73m  20m S 40.5  7.3   1:39.73 firefox           
 4715 root      20   0 80504  21m 7100 S  1.3  2.1   1:34.31 Xorg              
 6372 nick      20   0  2412 1128  884 R  0.7  0.1   0:00.22 top               
    1 root      20   0  3056 1888  564 S  0.0  0.2   0:02.26 init              
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd          
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0       
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.06 ksoftirqd/0       
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0        
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 events/0          
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 khelper           
   46 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0     
   48 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 kblockd/0         
   50 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid            
   51 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify      
  129 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cqueue            
  133 root      15  -5     0    0    0 S  0.0  0.0   0:00.32 kseriod           
  167 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush 
```idk if it's just peaking or whatever.  Doesn't happen on my mac... possibly because it's more stable as a desktop computer..? Whatever... i just wanna know how to speed this thing up lol.  Any ideas?

~Nick~

---

### Post by Crio on 2008-11-13
2johanhartman: to switch off acpid go to System->Administration->Services and remove tick against ACPI entry. You get rid of the problem but you probably lose power management features (that is what ACPI should be responsible for) - fan control, hibernation, etc.

2Link64x: Your top does not show any excessive CPU usage.  'id' means idle, i.e. these are unused CPU power. Watch for 'us' (user) and 'sy' (system, here meaning kernel) percentages.
Differences between the first and later top screenshots are probably due to sorting. You change it by pressing keys on the keyboard - see 'man top'.

  

2spibou: thank you for suggestion, but now I'm really stretching my knowledge. Can you guide me, please?  
Below is output of the following command:

sudo strace /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
 
I don't understand what all that close() are about, but the only real problem I see is 

acpid: can't open /proc/acpi/event: Device or resource busy

Now, how to find out what is locking it?

```

execve("/usr/sbin/acpid", ["/usr/sbin/acpid", "-c", "/etc/acpi/events", "-s", "/var/run/acpid.socket", "1"], [/* 16 vars */]) = 0
brk(0)                                  = 0x8fa7000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f8d000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=57831, ...}) = 0
mmap2(NULL, 57831, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f7e000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\340g\1"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=1425800, ...}) = 0
mmap2(NULL, 1431152, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7e20000
mmap2(0xb7f78000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x158) = 0xb7f78000
mmap2(0xb7f7b000, 9840, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7f7b000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7e1f000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb7e1f6b0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0xb7f78000, 8192, PROT_READ)   = 0
mprotect(0x804d000, 4096, PROT_READ)    = 0
mprotect(0xb7faa000, 4096, PROT_READ)   = 0
munmap(0xb7f7e000, 57831)               = 0
getrlimit(RLIMIT_NOFILE, {rlim_cur=1024, rlim_max=1024}) = 0
close(3)                                = -1 EBADF (Bad file descriptor)
close(4)                                = -1 EBADF (Bad file descriptor)
...
*here goes another 1018 lines with increasing numbers*
...
close(1022)                             = -1 EBADF (Bad file descriptor)
close(1023)                             = -1 EBADF (Bad file descriptor)
open("/proc/acpi/event", O_RDONLY)      = -1 EBUSY (Device or resource busy)
write(2, "acpid: can\'t open /proc/acpi/eve"..., 60acpid: can't open /proc/acpi/event: Device or resource busy
) = 60
exit_group(1)                           = ?
Process 14616 detached

```

---

### Post by Crio on 2008-11-13
Bingo!

It occured to me to run acpid in debug mode

```

 sudo /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket -d

```

(it stays in foreground and logs to console and I found that it constantly receives an event "hotkey ATKD 0000005f" which matches to ASUS "WAN on" key pressed.

```

acpid: received event "hotkey ATKD 0000005f 0000bd8f"
acpid: rule from /etc/acpi/events/asus-wireless-on matched
acpid: executing action "/etc/acpi/asus-wireless.sh on"
BEGIN HANDLER MESSAGES
END HANDLER MESSAGES
acpid: action exited with status 0
acpid: rule from /etc/acpi/events/asus-wireless-2 matched
acpid: executing action "/etc/acpi/asus-wireless-2.sh hotkey ATKD 0000005f 0000bd8f"
BEGIN HANDLER MESSAGES
END HANDLER MESSAGES
acpid: action exited with status 0
acpid: 2 total rules matched
acpid: completed event "hotkey ATKD 0000005f 0000bd8f"

```

Since my laptop is Toshiba I figured out that it has nothing to do with me and commented out contents of /etc/acpi/events/asus-wireless-2 and /etc/acpi/events/asus-wireless-on  (probably, I could just delete them).

CPU usage problem gone! Thank you, people!

It would be interesting to find out where the event comes from (and get rid of it). Any ideas how to do that? 
It is quite possible that it is a hardware problem - the keyboard suffered a coffee spill some time ago - though no other malfunctions is evident.

---

### Post by johanhartman on 2008-11-13
> **Crio said:**
> Bingo!

It occured to me to run acpid in debug mode

```

 sudo /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket -d

```

(it stays in foreground and logs to console and I found that it constantly receives an event "hotkey ATKD 0000005f" which matches to ASUS "WAN on" key pressed.

```

acpid: received event "hotkey ATKD 0000005f 0000bd8f"
acpid: rule from /etc/acpi/events/asus-wireless-on matched
acpid: executing action "/etc/acpi/asus-wireless.sh on"
BEGIN HANDLER MESSAGES
END HANDLER MESSAGES
acpid: action exited with status 0
acpid: rule from /etc/acpi/events/asus-wireless-2 matched
acpid: executing action "/etc/acpi/asus-wireless-2.sh hotkey ATKD 0000005f 0000bd8f"
BEGIN HANDLER MESSAGES
END HANDLER MESSAGES
acpid: action exited with status 0
acpid: 2 total rules matched
acpid: completed event "hotkey ATKD 0000005f 0000bd8f"

```

Since my laptop is Toshiba I figured out that it has nothing to do with me and commented out contents of /etc/acpi/events/asus-wireless-2 and /etc/acpi/events/asus-wireless-on  (probably, I could just delete them).

CPU usage problem gone! Thank you, people!

It would be interesting to find out where the event comes from (and get rid of it). Any ideas how to do that? 
It is quite possible that it is a hardware problem - the keyboard suffered a coffee spill some time ago - though no other malfunctions is evident.

You're a GENIUS, thank you, that solved my problem too. Incidentally, my keyboard also recently suffered a coffee dip, but that was before upgrading to intrepid and I hadn't noticed any problems before upgrading. Since upgrading my NumLock sometimes turn on spontaneously, this may be related. Anyway, have you filed a bug yet?

:popcorn:

---

### Post by Link64x on 2008-11-13
man, wish I wasn't so new to this lol.  When I put in the code that fixed both of your problems, i'm still getting the error message:

```
acpid: can't open /proc/acpi/event: Device or resource busy
```

mebbe i'm just retarded.  idk.  lol.  i'm thinking i should just go back to windows xD i'd have an easier time just sticking to what I know.

[EDIT:] yep, i'm retarded.  Was a simple video card driver error that was slowing me down.  Reinstalled the driver and everything works fine xD.  Thx for attempting to help haha.

~Nick~

---

### Post by spibou on 2008-11-13
Did you already have acpid running when you tried the above?

---

### Post by Anistruk on 2009-01-27
Big thanks [Crio](http://ubuntuforums.org/member.php?u=704477)!!!

Finally have my Ubunto at 100%!!!

Didn't get the code for the debug mode to work, but comment the specified lines and the cpu is back to normal!!

Best regards!

---

### Post by Mike Greenwood on 2009-02-28
Similar Problem


top - 11:00:45 up  2:39,  2 users,  load average: 0.69, 0.91, 0.89
Tasks: 109 total,   2 running, 107 sleeping,   0 stopped,   0 zombie
Cpu(s): 52.1%us, 40.6%sy,  0.0%ni,  7.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    318112k total,   306568k used,    11544k free,     7212k buffers
Swap:   473876k total,     9224k used,   464652k free,    79404k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                             
 5042 root      20   0  101m  18m 6936 R 47.4  5.9  44:02.96 Xorg                                                
 5676 mike      20   0 37152  17m  12m S 37.2  5.8  22:02.27 gnome-system-mo                                     
 5753 mike      20   0  200m  79m  25m S  7.2 25.5  16:13.74 firefox                                             
 5473 mike      20   0 23196  11m 8832 S  0.7  3.6   0:03.44 trashapplet                                         
 8075 mike      20   0 77008  21m  12m S  0.7  6.8   0:09.26 gnome-terminal                                      
 8099 mike      20   0  2412 1136  876 R  0.7  0.4   0:01.54 top                                                 
    1 root      20   0  3056 1860  540 S  0.0  0.6   0:02.96 init                                                
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 kthreadd                                            
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                         
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.42 ksoftirqd/0                                         
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                          
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.46 events/0                                            
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 khelper                                             
   46 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0                                       
   48 root      15  -5     0    0    0 S  0.0  0.0   0:00.30 kblockd/0                                           
   50 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                              
   51 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                        
  111 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cqueue                                              
  115 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                                             
  149 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush                                             
  150 root      20   0     0    0    0 S  0.0  0.0   0:00.36 pdflush                                             
  151 root      15  -5     0    0    0 S  0.0  0.0   0:00.82 kswapd0                                             
  195 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                               
 1232 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                       
 1233 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                               
 1240 root      15  -5     0    0    0 S  0.0  0.0   0:00.86 ata/0                                               
 1242 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                             
 1293 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                                           
 1294 root      15  -5     0    0    0 S  0.0  0.0   0:01.34 scsi_eh_1                                           
 2027 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_4                                           
 2077 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 usb-storage                                         
 2082 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_5                                           
 2083 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 usb-storage                                         
 2133 root      15  -5     0    0    0 S  0.0  0.0   0:00.78 kjournald                                           
 2309 root      16  -4  2524  716  404 S  0.0  0.2   0:01.70 udevd                                               
 2479 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kgameportd

---

