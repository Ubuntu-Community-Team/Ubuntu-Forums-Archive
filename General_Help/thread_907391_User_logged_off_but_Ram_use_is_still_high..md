---
title: "User logged off but Ram use is still high."
date: 2008-09-01
forum: General Help
---

### Post by u-slayer on 2008-09-01
I had two users on my machine and I noticed that my ram was double normal. So I logged off the guest account and my ram was still high. I can't find what's using all the ram..

free -m:
```
             total       used       free     shared    buffers     cached
Mem:          3956       3929         26          0         25       2677
-/+ buffers/cache:       1227       2728
Swap:         4094         43       4050

```

1277 is twice normal.:shock: 30% of total ram.

top (Shift+M):
```
top - 12:07:23 up 1 day, 12:25,  6 users,  load average: 0.30, 0.30, 0.36
Tasks: 186 total,   1 running, 179 sleeping,   0 stopped,   6 zombie
Cpu(s):  6.7%us,  3.3%sy,  0.0%ni, 89.5%id,  0.2%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:   4050980k total,  4021364k used,    29616k free,    26108k buffers
Swap:  4192956k total,    44880k used,  4148076k free,  2738660k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
12707 slayer      20   0  811m 348m  19m S    1  8.8  14:01.29 deluge             
 6154 root        20   0  539m 152m  34m S    5  3.9  23:03.64 Xorg               
20372 slayer      20   0  532m 108m  26m S    1  2.7   0:16.41 firefox            
 7784 slayer      20   0  527m  61m  16m S    0  1.5   2:59.64 nautilus           
 6340 slayer      20   0  293m  56m  14m S    1  1.4   5:53.22 compiz.real        
 6272 slayer      20   0  327m  34m  15m S    0  0.9   0:38.41 gnome-panel        
20257 slayer      20   0  281m  28m  12m S    0  0.7   0:01.14 gnome-terminal     
20611 slayer      20   0  214m  26m  14m S    7  0.7   0:59.98 gnome-system-mo    
 6357 slayer      20   0  222m  25m  11m S    0  0.6   0:00.40 python             
10927 slayer      20   0  283m  23m  12m S    0  0.6   2:05.85 truecrypt          
 6359 slayer      20   0  202m  20m  10m S    0  0.5   0:28.68 nm-applet          
 6377 slayer      20   0  236m  17m  10m S    0  0.4   0:00.28 mixer_applet2      
14650 root        20   0 54640  17m 2144 S    0  0.4   0:00.12 SystemToolsBack    
 6175 slayer      20   0  210m  16m  10m S    0  0.4   0:01.78 gnome-session      
 6380 slayer      20   0  210m  16m 9832 S    0  0.4   0:02.76 gnome-keyboard-    
 6344 slayer      20   0  204m  16m 9.9m S    0  0.4   0:01.26 update-notifier    
 6423 slayer      20   0  149m  16m 8252 S    0  0.4   0:02.72 notification-da    
20327 lp          20   0  106m  15m 4380 S    0  0.4   0:00.18 gs                 
 6389 slayer      20   0  144m  14m 7964 S    0  0.4   0:20.34 gtk-window-deco    
 5440 debian-t    20   0 43660  13m 4764 S    0  0.3   0:17.88 tor                
11988 slayer      20   0  211m  12m 8356 S    0  0.3   0:00.10 seahorse-daemon    
 6351 slayer      20   0  274m  11m 9484 S    0  0.3   0:00.04 evolution-alarm    
 6244 slayer      20   0  247m  11m 8856 S    0  0.3   0:04.74 gnome-settings-    
 6354 slayer      39  19 76980  10m 2392 S    0  0.3   0:00.02 trackerd           
 6364 slayer      20   0  207m 8476 5704 S    0  0.2   0:00.86 gnome-power-man    

```

---

### Post by Peter09 on 2008-09-01
Ram is often used by a modern operating system to store data and code that may be used again (cos its fast access). So the amount of memory being used is not a good guide to 'real' usage. Unless you are using a lot of swap space on disk I would not worry about it.

PC

---

### Post by u-slayer on 2008-09-01
> **Peter09 said:**
> Ram is often used by a modern operating system to store data and code that may be used again (cos its fast access). So the amount of memory being used is not a good guide to 'real' usage. Unless you are using a lot of swap space on disk I would not worry about it.

PC

I know that. I was looking at the line that shows how much is being used by programs:

-/+ buffers/cache:       1227       2728

see: 1227MB of Ram. -- way too much.

---

### Post by monkeyking on 2008-09-01
Thats strange.
has it happened before or is it new.

I would just reboot,
and if it happens again.
I would start fixing it.

---

### Post by Oldsoldier2003 on 2008-09-01
> **u-slayer said:**
> I know that. I was looking at the line that shows how much is being used by programs:

-/+ buffers/cache:       1227       2728

see: 1227MB of Ram. -- way too much.

linux memory management is such that buffers and cache are often used and full. empty ram is wasted ram in the eyes of the devs.

---

### Post by monkeyking on 2008-09-02
> **Oldsoldier2003 said:**
> linux memory management is such that buffers and cache are often used and full. empty ram is wasted ram in the eyes of the devs.

I've heard this before but I don't think it is correct this is the free -m from 3 different machines
```

free -m
             total       used       free     shared    buffers     cached
Mem:          2017        930       1086          0        177        478
-/+ buffers/cache:        273       1743
Swap:         5906          0       5906


```

```
            total       used       free     shared    buffers     cached
Mem:          7997        331       7666          0         49        134
-/+ buffers/cache:        147       7850
Swap:        23422        194      23228
```

```

free -m
             total       used       free     shared    buffers     cached
Mem:         48394      19986      28408          0        191      19155
-/+ buffers/cache:        639      47755
Swap:        38523        141      38381


```

I do think slayer has a problem with a memory leak.
But unless it is persistent I wouldn't worry.

---

### Post by Oldsoldier2003 on 2008-09-02
while it is entirely possible he has a memory leak I'm with you I wouldnt worry. After any signifgant use of the machine the free command will start to show caching. for example this machine I am on now has 286 M free because it was rebooted recently. By tomorrow the stats will differ signifgantly because I'm going to compile a few programs while I sleep, and though nothing will be running the memory usage will be very high.

---

