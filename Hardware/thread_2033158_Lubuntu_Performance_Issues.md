---
title: "Lubuntu Performance Issues"
date: 2012-07-25
forum: Hardware
---

### Post by rduffee on 2012-07-25
I recently installed Lubuntu on the ageing machine of a friend of mine (Windows XP was terribly slow). Unfortunately, Lubuntu isn't any faster - the startup time takes several minutes, and there's severe lag when opening applications/menus or even just clicking and typing things. As it is, the computer is unusable. I think it's a problem of insufficient hardware, but I'm not sure. Is there anything I can do to speed up performance (without installing new hardware), or am I just out of luck?

Here's some relevant specs:

232MB RAM
839 Mhz Processor
16 MB Video Card


And the results of free and top:

```
free -m
             total       used       free     shared    buffers     cached
Mem:           227        221          5          0         30         81
-/+ buffers/cache:        109        117
Swap:          477          4        473
```

```
top - 14:59:04 up 22 min,  0 users,  load average: 3.26, 3.37, 2.54
Tasks: 107 total,   3 running, 103 sleeping,   0 stopped,   1 zombie
Cpu(s): 69.9%us, 28.2%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  1.9%si,  0.0%st
Mem:    232712k total,   223768k used,     8944k free,    10144k buffers
Swap:   489468k total,    22768k used,   466700k free,    49068k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1971 lynn      20   0  222m  55m  12m R 21.5 24.5   1:07.70 /usr/bin/python /us
 1526 lynn      20   0  152m  11m 8092 S 19.3  4.9   0:50.20 lxpanel --profile L
  919 root      20   0 68640  12m 4880 S 17.7  5.7   2:17.64 /usr/bin/X :0 -auth
 2555 lynn      20   0 13272 6652 2808 R 16.4  2.9   0:00.88 /usr/bin/python /us
 1618 lynn      20   0  161m  11m 8032 S 11.7  4.9   0:30.94 lxterminal         
   22 root      20   0     0    0    0 S  4.7  0.0   0:04.16 [kswapd0]          
 1784 lynn      20   0  155m  11m 8524 S  2.5  5.2   0:47.44 hardinfo           
 1541 lynn      20   0  159m 7652 5592 S  1.9  3.3   0:24.97 xfce4-power-manager
 1916 lynn      20   0  2816 1024  784 R  1.3  0.4   0:09.62 top                
 1980 lynn      20   0  189m  27m  17m S  0.6 12.3   0:49.08 abiword            
 2064 root      20   0     0    0    0 S  0.6  0.0   0:00.22 [kworker/0:2]      
  836 root      20   0  2600  704  656 S  0.3  0.3   0:00.18 cron               
 1521 lynn      20   0 16756 6544 4184 S  0.3  2.8   0:11.18 openbox --config-fi
 1589 lynn      20   0 20464 1864 1652 S  0.3  0.8   0:00.98 /usr/lib/gvfs/gvfs-
    1 root      20   0  3504 1548 1068 S  0.0  0.7   0:07.33 /sbin/init         
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.04 [kthreadd]         
    3 root      20   0     0    0    0 S  0.0  0.0   0:00.30 [ksoftirqd/0]   
```

Any help would be greatly appreciated. Thanks!

---

### Post by ahallubuntu on 2012-07-25
That hardware is very old and slow, and with only 256MB of RAM (looks like 24MB reserved for dedicated graphics), it's going to be pretty slow with any version of Ubuntu.

I'd try Puppy Linux instead:

[http://puppylinux.org/](http://puppylinux.org/)

Puppy loads into RAM and runs from there, but it's very small and compact and sure run on this machine for sure.  In fact, you don't have to "install" it at all - just boot the CD.  You can choose to save the state of things before you shut down (to the hard drive or a thumb drive); otherwise it's like an Ubuntu live CD.

Puppy is much less attractive and friendly than Ubuntu, but it usually works; you trade off some user-friendliness and polish for size and speed.  At least give it a try.

Now, if you CAN upgrade the RAM to 512MB if at all possible(!), that would make a huge difference - you would be able to run some version of Ubuntu and that would help Puppy too (better web browsing experience).  Upgrading the RAM may be cheaper and easier than you imagine - all depends.  If you provide more info about the exact hardware this is (model name, how many RAM slots are filled, etc.), we can help you decide how to upgrade and if it's even feasible.  But it might make more sense to find faster hardware, too.  Systems newer/faster than this one can often be had for little or nothing.

---

