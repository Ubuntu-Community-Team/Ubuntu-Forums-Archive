---
title: "Tweaking needed"
date: 2011-07-20
forum: Hardware
---

### Post by tech_girl on 2011-07-20
I'm using Ubuntu 11.04 AMD64 version on my Lenovo x120e.I was wondering if there are some background services or features that I can safely turn off. I find it a little sluggish especially since I have 8GB RAM. 

Thanks.

---

### Post by mastablasta on 2011-07-20
what graphics card do you have? is it sluggish by itself? something is definatelly wrong. a few parameters can be checked with 
 
top 
 
command in terminal. i use 1.3 GB, KDE, plenty effects on and it's really runnign fast.

---

### Post by tech_girl on 2011-07-20
Radeon HD 6310 Graphics. No it doesnt feel sluggish by itself....it only happens at times.
```



top - 23:27:49 up  2:07,  2 users,  load average: 0.03, 0.10, 0.07
Tasks: 158 total,   1 running, 156 sleeping,   0 stopped,   1 zombie
Cpu(s):  4.0%us,  4.0%sy,  0.5%ni, 91.5%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   7783640k total,  1610484k used,  6173156k free,   121552k buffers
Swap:  5858300k total,        0k used,  5858300k free,   833704k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                                                                             
 3229 kgtan     20   0  322m  16m  11m S    7  0.2   0:05.30 gnome-terminal                                                                                                                                                      
 1082 root      20   0  153m  28m 9780 S    5  0.4  10:57.03 Xorg                                                                                                                                                                
 3219 kgtan     25   5  865m  38m  20m S    1  0.5   0:01.78 chromium-browse                                                                                                                                                     
 3288 kgtan     20   0 19352 1340  956 R    0  0.0   0:01.05 top                                                                                                                                                                 
 3312 kgtan     20   0  648m  96m  65m S    0  1.3   0:11.58 soffice.bin                                                                                                                                                         
    1 root      20   0 23996 2176 1356 S    0  0.0   0:00.94 init                                                                                                                                                                
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                                                                                            
    3 root      20   0     0    0    0 S    0  0.0   0:02.30 ksoftirqd/0                                                                                                                                                         
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0                                                                                                                                                         
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1                                                                                                                                                         
    9 root      20   0     0    0    0 S    0  0.0   0:01.91 ksoftirqd/1                                                                                                                                                         
   11 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset                                                                                                                                                              
   12 root       0 -20     0    0    0 S    0  0.0   0:00.00 khelper                                                                                                                                                             
   13 root       0 -20     0    0    0 S    0  0.0   0:00.00 netns                                                                                                                                                               
   15 root      20   0     0    0    0 S    0  0.0   0:00.04 sync_supers                                                                                                                                                         
   16 root      20   0     0    0    0 S    0  0.0   0:00.00 bdi-default                                                                                                                                                         
   17 root       0 -20     0    0    0 S    0  0.0   0:00.00 kintegrityd                                                                                                                                                         
   18 root       0 -20     0    0    0 S    0  0.0   0:00.00 kblockd                                                                                                                                                             
   19 root       0 -20     0    0    0 S    0  0.0   0:00.00 kacpid                                                                                                                                                              
   20 root       0 -20     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                                                                                                                                        
   21 root       0 -20     0    0    0 S    0  0.0   0:00.00 kacpi_hotplug                                                                                                                                                       
   22 root       0 -20     0    0    0 S    0  0.0   0:00.00 ata_sff                                                                                                                                                             
   23 root      20   0     0    0    0 S    0  0.0   0:00.05 khubd                                                                                                                                                               
   24 root       0 -20     0    0    0 S    0  0.0   0:00.00 md                                                                                                                                                                  
   26 root      20   0     0    0    0 S    0  0.0   0:00.00 khungtaskd                                                                                                                                                          
   27 root      20   0     0    0    0 S    0  0.0   0:00.00 kswapd0                                                                                                                                                             
   28 root      25   5     0    0    0 S    0  0.0   0:00.00 ksmd                                                                                                                                                                
   29 root      20   0     0    0    0 S    0  0.0   0:00.00 fsnotify_mark                                                                                                                                                       
   30 root       0 -20     0    0    0 S    0  0.0   0:00.00 aio                                                                                                                                                                 
   31 root      20   0     0    0    0 S    0  0.0   0:00.00 ecryptfs-kthrea                                                                                                                                                     
   32 root       0 -20     0    0    0 S    0  0.0   0:00.00 crypto                                                                                                                                                              
   36 root       0 -20     0    0    0 S    0  0.0   0:00.00 kthrotld                                                                                                                                                            
   37 root       0 -20     0    0    0 S    0  0.0   0:00.00 kmpathd                                                                                                                                                             
   38 root       0 -20     0    0    0 S    0  0.0   0:00.00 kmpath_handlerd                                                                                                                                                     
   39 root       0 -20     0    0    0 S    0  0.0   0:00.00 kondemand                                                                                                                                                           
   40 root       0 -20     0    0    0 S    0  0.0   0:00.00 kconservative                                                                                                                                                       
  197 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_0                                                                                                                                                           
  210 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_1                                                                                                                                                           
  211 root      20   0     0    0    0 S    0  0.0   0:02.26 usb-storage                                                                                                                                                         
  228 root      20   0     0    0    0 S    0  0.0   0:00.45 jbd2/sda3-8                                                                                                                                                         
  229 root       0 -20     0    0    0 S    0  0.0   0:00.00 ext4-dio-unwrit                                                                                                                                                     
  281 root      20   0 17052  636  452 S    0  0.0   0:00.22 upstart-udev-br                                                                                                                                                     
  290 root      16  -4 21608 1132  332 S    0  0.0   0:00.15 udevd                                                                                                                                                               
  504 root       0 -20     0    0    0 S    0  0.0   0:00.00 kpsmoused                                                                                                                                                           

```

Does this look ok?

---

