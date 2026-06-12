---
title: "why are my system resources being pillaged?"
date: 2009-09-14
forum: Hardware
---

### Post by honey toast on 2009-09-14
Hi, I'm using a jaunty on my hp mini 1030nr and for some reason my cpu is being hammered by unseen processes. I cannot locate why or what is causing this, but I have a suspicion. I think that I am logged in as root, but I'm not sure how I would have done that, because I simply logged in to my mini the same way that I always do. In the event that I am logged in as root, then how would I not? What else can I do as a remedy for this? I'm plugged in at the library and the sound of my mini is getting me looks from people nearby. HELP!
Here is a paste of top...


top - 15:34:48 up 2 days,  4:19,  2 users,  load average: 1.40, 1.37, 1.17
Tasks: 128 total,   1 running, 127 sleeping,   0 stopped,   0 zombie
Cpu(s): 48.3%us,  3.9%sy,  0.0%ni, 47.5%id,  0.0%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:   2053532k total,   797636k used,  1255896k free,    33964k buffers
Swap:   714852k total,        0k used,   714852k free,   454160k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                         
 2722 root      20   0  311m  36m  10m S   57  1.8  26:17.31 Xorg                                                            
 6338 1000      20   0 39616  19m  13m S   41  1.0  13:43.51 gnome-system-mo                                                 
 6851 1000      20   0  152m  84m  48m S    6  4.2   1:38.95 avastgui                                                        
 7052 1000      20   0 34000  14m 9480 S    2  0.7   0:02.63 gnome-terminal                                                  
 5728 1000      20   0  185m  94m  24m S    1  4.7   8:22.33 firefox                                                         
 7179 1000      20   0  2448 1188  912 R    1  0.1   0:00.73 top                                                             
 2651 root      20   0  5180 1796 1588 S    0  0.1   0:01.06 hald-addon-stor                                                 
 3324 1000      20   0 23984  10m 8644 S    0  0.5   1:00.06 multiload-apple                                                 
    1 root      20   0  3084 1884  564 S    0  0.1   0:01.72 init                                                            
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                        
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.02 migration/0                                                     
    4 root      15  -5     0    0    0 S    0  0.0   0:01.96 ksoftirqd/0                                                     
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                      
    9 root      15  -5     0    0    0 S    0  0.0   0:00.16 events/0                                                        
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper                                                         
   12 root      RT  -5     0    0    0 S    0  0.0   0:00.00 kstop/0                                                         
   14 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/0                                                   
   16 root      15  -5     0    0    0 S    0  0.0   0:00.07 kblockd/0                                                       
   18 root      15  -5     0    0    0 S    0  0.0   0:00.04 kacpid                                                          
   19 root      15  -5     0    0    0 S    0  0.0   0:00.01 kacpi_notify                                                    
   20 root      15  -5     0    0    0 S    0  0.0   0:00.00 cqueue                                                          
   21 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata/0                                                           
   23 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata_aux

---

### Post by Whiffle on 2009-09-14
I see Xorg and gnome-system monitor taking up quite a bit...not much other than that.

---

### Post by cariboo on 2009-09-14
Turn off the gnome-system-monitor as it adds quite a bit of overhead, also shutdown avast, as it isn't doing you any good scanning for windows viruses.

---

### Post by utnubuuser on 2009-09-14
You could try googling your video-card as well.  If your card isn't configured properly it'll hog resources.

---

