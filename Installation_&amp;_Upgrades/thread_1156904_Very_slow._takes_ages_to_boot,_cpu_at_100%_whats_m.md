---
title: "Very slow. takes ages to boot, cpu at 100% whats my best option?"
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by Paul VW on 2009-05-12
I have had ubuntu on this comp since about version 6, and since version 8 (and now 9) it has been getting slower and slower, the system monitor says the cpu is running at 100% all the time!!

how do I fix this? do I wipe and re-install? or is there another way round this?

I think the computer is fine, as it runs windows xp without a hitch (cpu usages is running at 10%ish)

---

### Post by kpkeerthi on 2009-05-12
You can check whats occupying your CPU using the **top** command. Press 'q' to quit and post the output here.

---

### Post by Paul VW on 2009-05-12
thanks for the reply, here are the results:
> paul@paul-desktop:~$ TOP
bash: TOP: command not found
paul@paul-desktop:~$ top

top - 17:53:42 up 10 min,  2 users,  load average: 2.43, 2.41, 1.29
Tasks: 126 total,   3 running, 123 sleeping,   0 stopped,   0 zombie
Cpu(s): 52.1%us, 17.8%sy, 29.4%ni,  0.0%id,  0.0%wa,  0.3%hi,  0.3%si,  0.0%st
Mem:    766188k total,   750916k used,    15272k free,   319820k buffers
Swap:  1726948k total,        0k used,  1726948k free,   209416k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 3315 paul      20   0  3100 1352  660 S 22.9  0.2   1:40.51 dbus-daemon        
 3465 paul      39  19 27860  10m 5616 R 19.9  1.4   1:19.24 tracker-indexer    
 3396 paul      20   0 28060  14m 8140 S 19.3  1.9   1:14.02 python             
 3378 paul      39  19 51892  10m 4968 S 15.6  1.3   0:58.87 trackerd           
 2819 root      20   0  154m  16m 7488 S  9.0  2.1   0:08.18 Xorg               
 3387 paul      20   0 19252 7276 5944 S  8.6  0.9   0:35.90 tracker-applet     
 3794 paul      20   0 45324  13m  10m R  3.3  1.9   0:00.42 gnome-terminal     
 2744 root      20   0  5180 1800 1588 S  0.3  0.2   0:00.04 hald-addon-stor    
 3530 paul      20   0  213m  81m  26m S  0.3 10.9   0:23.57 firefox            
    1 root      20   0  3084 1888  564 S  0.0  0.2   0:01.38 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.13 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.01 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
    8 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 kstop/0            



---

### Post by kpkeerthi on 2009-05-12
When posting command outputs, enclose it within [code] tags.

---

### Post by Paul VW on 2009-05-13
ok here goes again

```
paul@paul-desktop:~$ top

top - 12:15:52 up 9 min,  2 users,  load average: 3.04, 2.65, 1.35
Tasks: 129 total,   3 running, 126 sleeping,   0 stopped,   0 zombie
Cpu(s): 50.3%us, 20.7%sy, 29.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    766188k total,   648404k used,   117784k free,    62052k buffers
Swap:  1726948k total,        0k used,  1726948k free,   335288k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 3341 paul      20   0  3072 1316  660 S 28.2  0.2   1:19.31 dbus-daemon        
 3485 paul      39  19 27876  10m 5612 R 20.9  1.4   1:05.33 tracker-indexer    
 3415 paul      20   0 28060  14m 8140 S 18.9  1.9   1:00.91 python             
 3397 paul      39  19 55108  11m 4960 S 16.6  1.5   0:46.77 trackerd           
 3407 paul      20   0 19384 7292 5908 S  9.3  1.0   0:27.88 tracker-applet     
 2838 root      20   0  158m  18m 7400 S  3.3  2.5   0:16.38 Xorg               
 3540 paul      20   0  276m 102m  28m S  2.7 13.8   0:40.91 firefox            
 3870 paul      20   0 45780  14m  10m R  0.7  1.9   0:00.51 gnome-terminal     
    1 root      20   0  3084 1888  564 S  0.0  0.2   0:01.38 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.10 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.01 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
    8 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 kstop/0            
    9 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0      
paul@paul-desktop:~$ 



```

---

### Post by Bark on 2009-05-13
This looks like some kind of bug in your system. The easiest way to resolve it may be to reinstall Ubuntu.

The dbus thing seems to be flaky, from my experience, and goes awry after upgrades.

---

### Post by kpkeerthi on 2009-05-13
No wait. No need to reinstall. There is nothing wrong I could see from the top command output. 

You seem to have [tracker]("http://packages.ubuntu.com/jaunty/tracker-search-tool") enabled and it is busy indexing your files. You can read about it [here]("http://projects.gnome.org/tracker/"). In my experience, I find tracker using up a lot of cpu and a lot of users have reported the issue in the forum. You may uninstall it using:
```
sudo apt-get purge tracker-search-tool
``` and reboot.

Or disable it completely from starting under System -> Preferences -> Startup Applications.

Or let the indexer run for a few hours (the time may vary depending on how much data you have) and see if there is an improvement.

My suggestion would be... uninstall tracker-search-tool and user Places -> Search for Files if you need to search something on your computer.

---

### Post by Paul VW on 2009-05-13
thanks for that :D:D it has seemed to have worked! much better now
```
paul@paul-desktop:~$ top

top - 17:40:55 up 3 min,  2 users,  load average: 1.21, 0.63, 0.25
Tasks: 122 total,   3 running, 119 sleeping,   0 stopped,   0 zombie
Cpu(s):  6.0%us,  0.7%sy,  0.0%ni, 93.4%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    766188k total,   526668k used,   239520k free,    56316k buffers
Swap:  1726948k total,        0k used,  1726948k free,   207028k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 2829 root      20   0  184m  44m 7436 S  4.0  5.9   0:12.26 Xorg               
 3491 paul      20   0  231m 100m  26m R  1.3 13.4   0:16.52 firefox            
 3794 paul      20   0  2448 1180  912 R  0.3  0.2   0:00.04 top                
    1 root      20   0  3084 1884  564 S  0.0  0.2   0:01.39 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.06 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.01 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
    8 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 kstop/0            
    9 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0      
   10 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 kblockd/0          
   11 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   12 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
   13 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cqueue             

```

---

