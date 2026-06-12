---
title: "Memory size not fully detected."
date: 2011-12-14
forum: Hardware
---

### Post by Ifaistos on 2011-12-14
Hello everyone :)

Since I upgraded to 9.11 I had problems with my memory.  As you can see in my signature I had 2 GB of Geil, and all of sudden it wasn't enough...  I was disappointed with 9.11.  It seems that it needed more memory and it certainly made my system slower.

I decided to upgrade my memory to another 2 GB.  The memory arrived today and I installed it.  When I rebooted the machine it was detected correctly by the BIOS.  However when I logged on Linux only 3.2 GB are detected.  Now before you go ahead and tell me that I have the 32 bit version, I will tell you that I have been using the 64 bit version for years now.  But just to be sure I double checked and I do have the 64 bit version.

The truth is that my computer is way much faster now!  But I want to know why the memory is not detected.  I can think of two things.

1. The memory is not fully compatible with my Geil?

Is there a way I could check that?  Is there some software that could help me understand and detect memory issues?

2. The memory is correctly detected and used by linux, only reported erroneously.  (Most probable)

I am using the system monitor icons and visually I know the load of my machine.  The way system monitor depicts it, it approximately half of what it was before.  So judging only visually, (although system monitor reports 3.2 GB as well) I assume that the memory is detected as 4GB and used correctly by my 64 bit system, but there is a bug and the memory is reported only at 3.2 GB.

That's all I can think for now.  Any help would be greatly appreciated.

Thank you all in advance for your help :-)

---

### Post by Ifaistos on 2011-12-14
bump :-)

---

### Post by wolfen69 on 2011-12-14
Do
```
top
```
in a terminal and copy & paste the info in the top part here.

---

### Post by Ifaistos on 2011-12-15
top - 08:33:27 up 23:35,  1 user,  load average: 0.26, 0.20, 0.17
top - 08:33:27 up 23:35,  1 user,  load average: 0.26, 0.20, 0.17
Tasks: 166 total,   1 running, 162 sleeping,   0 stopped,   3 zombie
Cpu(s): 17.7%us,  6.5%sy,  1.6%ni, 74.2%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3315836k total,  3134384k used,   181452k free,   100000k buffers
Swap:  2980052k total,    92964k used,  2887088k free,   343256k cached
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                      
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                      
 2046 evans     20   0 1975m 1.2g  12m S   16 38.0  37:32.28 chrome                                                       
 1326 root      20   0  164m  14m 5704 S   10  0.5  26:56.19 Xorg                                                         
 5365 evans     20   0  311m  17m  11m S    6  0.5   0:01.08 gnome-terminal                                               
 5372 evans     20   0 21460 1368  960 R    6  0.0   0:00.53 top                                                          
 1842 evans     20   0  313m  51m 8968 S    3  1.6   2:50.40 ubuntuone-syncd                                              
 1863 evans     20   0  287m  12m 8600 S    3  0.4   0:04.39 update-notifier                                              
 5081 evans     30  10  415m  69m  34m S    3  2.1   0:13.94 update-manager                                               
 5353 root      20   0 29888 2104 1768 S    3  0.1   0:01.69 http                                                         
    1 root      20   0 24180 1844 1116 S    0  0.1   0:00.79 init                                                         
    2 root      20   0     0    0    0 S    0  0.0   0:00.04 kthreadd                                                     
    3 root      20   0     0    0    0 S    0  0.0   0:10.24 ksoftirqd/0                                                  
    5 root      20   0     0    0    0 S    0  0.0   0:00.44 kworker/u:0                                                  
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0                                                  
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1                                                  
    9 root      20   0     0    0    0 S    0  0.0   0:32.39 ksoftirqd/1                                                  
   11 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset                                                       
   12 root       0 -20     0    0    0 S    0  0.0   0:00.00 khelper                                                      
   13 root       0 -20     0    0    0 S    0  0.0   0:00.00 netns                                                        
   15 root      20   0     0    0    0 S    0  0.0   0:00.19 sync_supers                                                  
   16 root      20   0     0    0    0 S    0  0.0   0:00.00 bdi-default                                                  
   17 root       0 -20     0    0    0 S    0  0.0   0:00.00 kintegrityd                                                  
   18 root       0 -20     0    0    0 S    0  0.0   0:00.00 kblockd                                                      
   19 root       0 -20     0    0    0 S    0  0.0   0:00.00 ata_sff                                                      
   20 root      20   0     0    0    0 S    0  0.0   0:00.00 khubd                                                        
   21 root       0 -20     0    0    0 S    0  0.0   0:00.00 md                                                           
   47 root      20   0     0    0    0 S    0  0.0   0:00.06 khungtaskd                                                   
   48 root      20   0     0    0    0 S    0  0.0   0:02.03 kswapd0                                                      
   49 root      25   5     0    0    0 S    0  0.0   0:00.00 ksmd                                                         
   50 root      39  19     0    0    0 S    0  0.0   0:00.00 khugepaged                                                   
   51 root      20   0     0    0    0 S    0  0.0   0:00.68 fsnotify_mark                                                
   52 root      20   0     0    0    0 S    0  0.0   0:00.00 ecryptfs-kthrea                                              
   53 root       0 -20     0    0    0 S    0  0.0   0:00.00 crypto                                                       
   61 root       0 -20     0    0    0 S    0  0.0   0:00.00 kthrotld                                                     
top - 08:33:27 up 23:35,  1 user,  load average: 0.26, 0.20, 0.17
Tasks: 166 total,   4 running, 159 sleeping,   0 stopped,   3 zombie
Cpu(s): 54.5%us, 27.3%sy,  0.0%ni, 18.2%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3315836k total,  3134368k used,   181468k free,   100000k buffers
Swap:  2980052k total,    92964k used,  2887088k free,   343316k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                     
 5365 evans     20   0  311m  17m  11m R   59  0.5   0:01.11 gnome-terminal                                               306 root      20   0     0    0    0 S    0  0.0   0:00.88 jbd2/sda1-8                                                
 1326 root      20   0  164m  14m 5704 S   39  0.5  26:56.21 Xorg                                                         364 root      20   0 17096  528  416 S    0  0.0   0:00.15 upstart-udev-br                                            
 1692 evans     20   0  382m  14m   9m R   20  0.4   0:41.17 metacity                                                     645 root       0 -20     0    0    0 S    0  0.0   0:00.00 edac-poller                                                
 5354 root      20   0 29888 2096 1752 S   20  0.1   0:00.73 http                                                         755 root       0 -20     0    0    0 S    0  0.0   0:00.00 ext4-dio-unwrit                                            
 5372 evans     20   0 21460 1368  960 R   20  0.0   0:00.54 top                                                          852 root      20   0     0    0    0 S    0  0.0   0:00.00 jbd2/sdc1-8                                                
    1 root      20   0 24180 1844 1116 S    0  0.1   0:00.79 init                                                         872 root       0 -20     0    0    0 S    0  0.0   0:00.00 hd-audio0                                                  
    2 root      20   0     0    0    0 S    0  0.0   0:00.04 kthreadd                                                     884 root      20   0 93760 1664 1328 S    0  0.1   0:00.32 smbd                                                       
    3 root      20   0     0    0    0 S    0  0.0   0:10.24 ksoftirqd/0                                                  916 messageb  20   0 25312 2232 1104 S    0  0.1   0:05.90 dbus-daemon                                                
    5 root      20   0     0    0    0 S    0  0.0   0:00.44 kworker/u:0                                                  927 root      20   0  160m 3392 2884 S    0  0.1   0:00.42 NetworkManager                                             
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0                                                  942 avahi     20   0 32132  164  132 S    0  0.0   0:00.00 avahi-daemon                                               
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1                                                  root      20   0  135m 4060 2896 S    0  0.1   0:00.56 polkitd                                                
    9 root      20   0     0    0    0 S    0  0.0   0:32.39 ksoftirqd/1                                                  root      20   0  4180  500  496 S    0  0.0   0:00.00 getty                                                  
   11 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset                                                       root      20   0  4180  500  496 S    0  0.0   0:00.00 getty                                                  
   12 root       0 -20     0    0    0 S    0  0.0   0:00.00 khelper                                                      root      20   0  4328  520  516 S    0  0.0   0:00.00 acpid                                                  
   13 root       0 -20     0    0    0 S    0  0.0   0:00.00 netns                                                        root      20   0 18976  820  744 S    0  0.0   0:00.11 cron                                                   
   15 root      20   0     0    0    0 S    0  0.0   0:00.19 sync_supers                                                  root      20   0  7128  728  632 S    0  0.0   0:00.00 dhclient                                               
   16 root      20   0     0    0    0 S    0  0.0   0:00.00 bdi-default                                                  root      20   0 23032 1020 1020 S    0  0.0   0:00.00 bluetoothd                                             
   17 root       0 -20     0    0    0 S    0  0.0   0:00.00 kintegrityd                                                  root      10 -10     0    0    0 S    0  0.0   0:00.00 krfcommd                                               
   18 root       0 -20     0    0    0 S    0  0.0   0:00.00 kblockd                                                      root      20   0     0    0    0 S    0  0.0   0:02.81 flush-8:0                                              
   19 root       0 -20     0    0    0 S    0  0.0   0:00.00 ata_sff                                                      root      20   0 63696  452  376 S    0  0.0   0:06.24 nmbd                                                   
   20 root      20   0     0    0    0 S    0  0.0   0:00.00 khubd                                                        root      20   0 70960 2064 1580 S    0  0.1   0:00.19 cupsd                                                  
   21 root       0 -20     0    0    0 S    0  0.0   0:00.00 md                                                           root      20   0  124m 2884 2592 S    0  0.1   0:00.14 console-kit-dae                                        
   47 root      20   0     0    0    0 S    0  0.0   0:00.06 khungtaskd                                                  
   48 root      20   0     0    0    0 S    0  0.0   0:02.03 kswapd0                                                     
   49 root      25   5     0    0    0 S    0  0.0   0:00.00 ksmd                                                        
   50 root      39  19     0    0    0 S    0  0.0   0:00.00 khugepaged                                                  
   51 root      20   0     0    0    0 S    0  0.0   0:00.68 fsnotify_mark                                               
   52 root      20   0     0    0    0 S    0  0.0   0:00.00 ecryptfs-kthrea                                             
   53 root       0 -20     0    0    0 S    0  0.0   0:00.00 crypto                                                      
   61 root       0 -20     0    0    0 S    0  0.0   0:00.00 kthrotld                                                    
  210 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_0                                                   
  211 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_1                                                   
  212 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_2                                                   
  213 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_3                                                   
  214 root      20   0     0    0    0 S    0  0.0   0:00.02 kworker/u:2                                                 
  217 root      20   0     0    0    0 S    0  0.0   0:08.33 scsi_eh_4                                                   
  219 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_5                                                   
  303 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_6                                                   
  304 root      20   0     0    0    0 S    0  0.0   0:19.02 usb-storage                                                 
  306 root      20   0     0    0    0 S    0  0.0   0:00.88 jbd2/sda1-8                                                 
  307 root       0 -20     0    0    0 S    0  0.0   0:00.00 ext4-dio-unwrit                                             
  364 root      20   0 17096  528  416 S    0  0.0   0:00.15 upstart-udev-br                                             
  368 root      20   0 21664  680  676 S    0  0.0   0:00.12 udevd                                                  top - 08:33:28 up 23:35,  1 user,  load average: 0.26, 0.20, 0.17
Tasks: 166 total,   7 running, 156 sleeping,   0 stopped,   3 zombie
Cpu(s): 70.0%us, 15.0%sy,  0.0%ni, 15.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3315836k total,  3134368k used,   181468k free,   100000k buffers
Swap:  2980052k total,    92964k used,  2887088k free,   343316k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                               
 5365 evans     20   0  311m  17m  11m R   59  0.5   0:01.17 gnome-terminal                                         1326 root      20   0  164m  14m 5704 R   39  0.5  26:56.25 Xorg                                                  
 2014 evans     20   0 1304m 116m  21m R   29  3.6  13:35.53 chrome                                                 1692 evans     20   0  382m  14m   9m R   20  0.4   0:41.19 metacity                                              
 5372 evans     20   0 21460 1368  960 R   20  0.0   0:00.56 top                                                    1704 evans     20   0  458m  31m  10m S   10  1.0   2:22.13 gnome-panel                                           
    1 root      20   0 24180 1844 1116 S    0  0.1   0:00.79 init                                                      2 root      20   0     0    0    0 S    0  0.0   0:00.04 kthreadd                                              
    3 root      20   0     0    0    0 S    0  0.0   0:10.24 ksoftirqd/0                                               5 root      20   0     0    0    0 S    0  0.0   0:00.44 kworker/u:0                                           
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0                                               7 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1                                           
    9 root      20   0     0    0    0 S    0  0.0   0:32.39 ksoftirqd/1                                              11 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset                                                
   12 root       0 -20     0    0    0 S    0  0.0   0:00.00 khelper                                                  13 root       0 -20     0    0    0 S    0  0.0   0:00.00 netns                                                 
   15 root      20   0     0    0    0 S    0  0.0   0:00.19 sync_supers                                              16 root      20   0     0    0    0 S    0  0.0   0:00.00 bdi-default                                           
   17 root       0 -20     0    0    0 S    0  0.0   0:00.00 kintegrityd                                              18 root       0 -20     0    0    0 S    0  0.0   0:00.00 kblockd                                               
   19 root       0 -20     0    0    0 S    0  0.0   0:00.00 ata_sff                                                  20 root      20   0     0    0    0 S    0  0.0   0:00.00 khubd                                                 
   21 root       0 -20     0    0    0 S    0  0.0   0:00.00 md                                                       47 root      20   0     0    0    0 S    0  0.0   0:00.06 khungtaskd                                            
   48 root      20   0     0    0    0 S    0  0.0   0:02.03 kswapd0                                                  49 root      25   5     0    0    0 S    0  0.0   0:00.00 ksmd                                                  
   50 root      39  19     0    0    0 S    0  0.0   0:00.00 khugepaged                                               51 root      20   0     0    0    0 S    0  0.0   0:00.68 fsnotify_mark                                         
   52 root      20   0     0    0    0 S    0  0.0   0:00.00 ecryptfs-kthrea                                          53 root       0 -20     0    0    0 S    0  0.0   0:00.00 crypto                                                
   61 root       0 -20     0    0    0 S    0  0.0   0:00.00 kthrotld                                                210 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_0                                             
  211 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_1                                                 
  212 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_2                                                 
  213 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_3                                                 
  214 root      20   0     0    0    0 S    0  0.0   0:00.02 kworker/u:2                                               
  217 root      20   0     0    0    0 S    0  0.0   0:08.33 scsi_eh_4                                            top - 08:33:28 up 23:35,  1 user,  load average: 0.26, 0.20, 0.17
Tasks: 166 total,   5 running, 158 sleeping,   0 stopped,   3 zombie
Cpu(s): 66.7%us, 22.2%sy,  0.0%ni,  0.0%id, 11.1%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3315836k total,  3134556k used,   181280k free,   100008k buffers
Swap:  2980052k total,    92964k used,  2887088k free,   343308k cached
  304 root      20   0     0    0    0 S    0  0.0   0:19.02 usb-storage                                            PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                              
 1692 evans     20   0  382m  14m   9m R   51  0.4   0:41.21 metacity                                              307 root       0 -20     0    0    0 S    0  0.0   0:00.00 ext4-dio-unwrit                                      5365 evans     20   0  311m  17m  11m R   51  0.5   0:01.19 gnome-terminal                                        364 root      20   0 17096  528  416 S    0  0.0   0:00.15 upstart-udev-br                                      1326 root      20   0  164m  14m 5704 R   26  0.5  26:56.26 Xorg                                                  368 root      20   0 21664  680  676 S    0  0.0   0:00.12 udevd                                                1780 evans     20   0  259m  10m 8448 S   26  0.3  10:41.39 multiload-apple                                       645 root       0 -20     0    0    0 S    0  0.0   0:00.00 edac-poller                                          2014 evans     20   0 1304m 116m  21m R   26  3.6  13:35.54 chrome                                                665 root       0 -20     0    0    0 S    0  0.0   0:00.00 kpsmoused                                            3552 evans     20   0  747m  26m  10m S   26  0.8  25:14.47 knotify4                                              727 root      20   0 21660  276  240 S    0  0.0   0:00.03 udevd                                                5372 evans     20   0 21460 1368  960 R   26  0.0   0:00.57 top                                                   747 root      20   0 21660  224  220 S    0  0.0   0:00.00 udevd                                                   1 root      20   0 24180 1844 1116 S    0  0.1   0:00.79 init                                                  754 root      20   0     0    0    0 S    0  0.0   0:03.97 jbd2/sda2-8                                             2 root      20   0     0    0    0 S    0  0.0   0:00.04 kthreadd                                              755 root       0 -20     0    0    0 S    0  0.0   0:00.00 ext4-dio-unwrit                                         3 root      20   0     0    0    0 S    0  0.0   0:10.24 ksoftirqd/0                                           835 root      20   0 15048  380  304 S    0  0.0   0:00.01 upstart-socket-                                         5 root      20   0     0    0    0 S    0  0.0   0:00.44 kworker/u:0                                           852 root      20   0     0    0    0 S    0  0.0   0:00.00 jbd2/sdc1-8                                             6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0                                           853 root       0 -20     0    0    0 S    0  0.0   0:00.00 ext4-dio-unwrit                                         7 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1                                           872 root       0 -20     0    0    0 S    0  0.0   0:00.00 hd-audio0                                               9 root      20   0     0    0    0 S    0  0.0   0:32.39 ksoftirqd/1                                           878 root      20   0 24692 2908  540 S    0  0.1   0:21.34 mount.ntfs                                             11 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset                                                884 root      20   0 93760 1664 1328 S    0  0.1   0:00.32 smbd                                                   12 root       0 -20     0    0    0 S    0  0.0   0:00.00 khelper                                               899 syslog    20   0  115m  752  752 S    0  0.0   0:10.84 rsyslogd                                               13 root       0 -20     0    0    0 S    0  0.0   0:00.00 netns                                                 916 messageb  20   0 25312 2232 1104 S    0  0.1   0:05.90 dbus-daemon                                            15 root      20   0     0    0    0 S    0  0.0   0:00.19 sync_supers                                           924 root      20   0 80820 2044 1928 S    0  0.1   0:00.03 modem-manager                                          16 root      20   0     0    0    0 S    0  0.0   0:00.00 bdi-default                                           927 root      20   0  160m 3392 2884 S    0  0.1   0:00.42 NetworkManager                                         17 root       0 -20     0    0    0 S    0  0.0   0:00.00 kintegrityd                                           928 avahi     20   0 32260 1184 1060 S    0  0.0   0:00.20 avahi-daemon                                           18 root       0 -20     0    0    0 S    0  0.0   0:00.00 kblockd                                               942 avahi     20   0 32132  164  132 S    0  0.0   0:00.00 avahi-daemon                                           19 root       0 -20     0    0    0 S    0  0.0   0:00.00 ata_sff                                               946 root      20   0 93760  332  248 S    0  0.0   0:00.00 smbd                                                   20 root      20   0     0    0    0 S    0  0.0   0:00.00 khubd                                                 950 root      20   0  135m 4060 2896 S    0  0.1   0:00.56 polkitd                                                21 root       0 -20     0    0    0 S    0  0.0   0:00.00 md                                                    982 root      20   0  4180  500  496 S    0  0.0   0:00.00 getty                                                  47 root      20   0     0    0    0 S    0  0.0   0:00.06 khungtaskd                                            987 root      20   0  4180  500  496 S    0  0.0   0:00.00 getty                                                  48 root      20   0     0    0    0 S    0  0.0   0:02.03 kswapd0                                              1000 root      20   0  4180  500  496 S    0  0.0   0:00.00 getty                                                  49 root      25   5     0    0    0 S    0  0.0   0:00.00 ksmd                                                 1001 root      20   0  4180  500  496 S    0  0.0   0:00.00 getty                                                  50 root      39  19     0    0    0 S    0  0.0   0:00.00 khugepaged                                           1003 root      20   0  4180  500  496 S    0  0.0   0:00.00 getty                                                  51 root      20   0     0    0    0 S    0  0.0   0:00.68 fsnotify_mark                                        1008 root      20   0  4328  520  516 S    0  0.0   0:00.00 acpid                                                  52 root      20   0     0    0    0 S    0  0.0   0:00.00 ecryptfs-kthrea                                      1012 root      20   0 15848  524  444 S    0  0.0   0:15.85 irqbalance                                             53 root       0 -20     0    0    0 S    0  0.0   0:00.00 crypto                                               1018 root      20   0 18976  820  744 S    0  0.0   0:00.11 cron                                                   61 root       0 -20     0    0    0 S    0  0.0   0:00.00 kthrotld                                             1019 daemon    20   0 16776  228  208 S    0  0.0   0:00.00 atd                                                   210 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_0                                            1031 root      20   0  7128  728  632 S    0  0.0   0:00.00 dhclient                                              211 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_1                                            1046 root      20   0 68104  628  544 S    0  0.0   0:00.00 winbindd                                              212 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_2                                            1065 root      20   0 23032 1020 1020 S    0  0.0   0:00.00 bluetoothd                                            213 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_3                                           top - 08:34:14 up 23:36,  1 user,  load average: 0.19, 0.19, 0.17
Tasks: 166 total,   1 running, 162 sleeping,   0 stopped,   3 zombie
Cpu(s): 15.6%us,  4.0%sy,  0.7%ni, 78.4%id,  1.2%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   3315836k total,  3146868k used,   168968k free,   100128k buffers
Swap:  2980052k total,    92964k used,  2887088k free,   352636k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                              
 5365 evans     20   0  311m  18m  11m S   12  0.6   0:03.74 gnome-terminal                                        1326 root      20   0  164m  14m 5180 S   11  0.4  26:58.21 Xorg                                                 
 1863 evans     20   0  287m  12m 8600 S    2  0.4   0:04.97 update-notifier                                       5353 root      20   0 29888 2104 1768 S    2  0.1   0:02.60 http                                                 
 3552 evans     20   0  747m  26m  10m S    2  0.8  25:15.34 knotify4                                              1704 evans     20   0  458m  31m  10m S    1  1.0   2:22.18 gnome-panel                                          
 2046 evans     20   0 1976m 1.2g  12m S    1 38.1  37:33.04 chrome                                                5081 evans     30  10  415m  69m  34m S    1  2.1   0:14.74 update-manager                                       
 2303 evans     20   0 1001m 136m  10m S    1  4.2  64:33.58 chrome                                                5354 root      20   0 29888 2096 1752 S    1  0.1   0:00.97 http                                                 
 1780 evans     20   0  259m  10m 8448 S    1  0.3  10:41.75 multiload-apple                                       5335 root      20   0  160m  63m  37m S    1  1.9   0:05.83 aptd                                                 
  916 messageb  20   0 25312 2232 1104 S    0  0.1   0:06.20 dbus-daemon                                           4317 evans     20   0 1149m 407m  20m S    0 12.6  14:24.08 thunderbird-bin                                      
 5372 evans     20   0 21460 1368  960 R    0  0.0   0:00.86 top                                                      1 root      20   0 24180 1844 1116 S    0  0.1   0:00.79 init                                                 
    2 root      20   0     0    0    0 S    0  0.0   0:00.04 kthreadd                                                 3 root      20   0     0    0    0 S    0  0.0   0:10.25 ksoftirqd/0                                          
    5 root      20   0     0    0    0 S    0  0.0   0:00.44 kworker/u:0                                              6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0                                          
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1                                              9 root      20   0     0    0    0 S    0  0.0   0:32.41 ksoftirqd/1                                          
   11 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset                                                  12 root       0 -20     0    0    0 S    0  0.0   0:00.00 khelper                                              
   13 root       0 -20     0    0    0 S    0  0.0   0:00.00 netns                                                   15 root      20   0     0    0    0 S    0  0.0   0:00.19 sync_supers                                          
   16 root      20   0     0    0    0 S    0  0.0   0:00.00 bdi-default                                             17 root       0 -20     0    0    0 S    0  0.0   0:00.00 kintegrityd                                          
   18 root       0 -20     0    0    0 S    0  0.0   0:00.00 kblockd                                                 19 root       0 -20     0    0    0 S    0  0.0   0:00.00 ata_sff                                              
   20 root      20   0     0    0    0 S    0  0.0   0:00.00 khubd                                                   21 root       0 -20     0    0    0 S    0  0.0   0:00.00 md                                                   
   47 root      20   0     0    0    0 S    0  0.0   0:00.06 khungtaskd                                              48 root      20   0     0    0    0 S    0  0.0   0:02.03 kswapd0                                              
   49 root      25   5     0    0    0 S    0  0.0   0:00.00 ksmd                                                    50 root      39  19     0    0    0 S    0  0.0   0:00.00 khugepaged                                           
   51 root      20   0     0    0    0 S    0  0.0   0:00.68 fsnotify_mark                                           52 root      20   0     0    0    0 S    0  0.0   0:00.00 ecryptfs-kthrea                                      
   53 root       0 -20     0    0    0 S    0  0.0   0:00.00 crypto                                                  61 root       0 -20     0    0    0 S    0  0.0   0:00.00 kthrotld                                             
  210 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_0                                              211 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_1                                            
  212 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_2                                              213 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_3                                            
  214 root      20   0     0    0    0 S    0  0.0   0:00.02 kworker/u:2                                            217 root      20   0     0    0    0 S    0  0.0   0:08.34 scsi_eh_4                                            
  219 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_5                                              303 root      20   0     0    0    0 S    0  0.0   0:00.00 scsi_eh_6                                            
  304 root      20   0     0    0    0 S    0  0.0   0:19.04 usb-storage                                            306 root      20   0     0    0    0 S    0  0.0   0:00.88 jbd2/sda1-8                                          
  307 root       0 -20     0    0    0 S    0  0.0   0:00.00 ext4-dio-unwrit                                        364 root      20   0 17096  528  416 S    0  0.0   0:00.15 upstart-udev-br                                      
  368 root      20   0 21664  680  676 S    0  0.0   0:00.12 udevd                                                  645 root       0 -20     0    0    0 S    0  0.0   0:00.00 edac-poller                                          
  665 root       0 -20     0    0    0 S    0  0.0   0:00.00 kpsmoused                                              727 root      20   0 21660  276  240 S    0  0.0   0:00.03 udevd                                                
  747 root      20   0 21660  224  220 S    0  0.0   0:00.00 udevd                                                  754 root      20   0     0    0    0 S    0  0.0   0:03.97 jbd2/sda2-8                                          
  755 root       0 -20     0    0    0 S    0  0.0   0:00.00 ext4-dio-unwrit                                        835 root      20   0 15048  380  304 S    0  0.0   0:00.01 upstart-socket-                                      
  852 root      20   0     0    0    0 S    0  0.0   0:00.00 jbd2/sdc1-8                                            853 root       0 -20     0    0    0 S    0  0.0   0:00.00 ext4-dio-unwrit                                      
  872 root       0 -20     0    0    0 S    0  0.0   0:00.00 hd-audio0                                              878 root      20   0 24692 2908  540 S    0  0.1   0:21.36 mount.ntfs                                           
  884 root      20   0 93760 1664 1328 S    0  0.1   0:00.32 smbd                                                   899 syslog    20   0  115m  752  752 S    0  0.0   0:10.84 rsyslogd                                             
  924 root      20   0 80820 2044 1928 S    0  0.1   0:00.03 modem-manager                                          927 root      20   0  160m 3392 2884 S    0  0.1   0:00.42 NetworkManager                                       
  928 avahi     20   0 32260 1184 1060 S    0  0.0   0:00.20 avahi-daemon                                           942 avahi     20   0 32132  164  132 S    0  0.0   0:00.00 avahi-daemon                                         
  946 root      20   0 93760  332  248 S    0  0.0   0:00.00 smbd                                                   950 root      20   0  135m 4060 2896 S    0  0.1   0:00.56 polkitd                                              
  982 root      20   0  4180  500  496 S    0  0.0   0:00.00 getty                                                
  987 root      20   0  4180  500  496 S    0  0.0   0:00.00 getty                                                
 1000 root      20   0  4180  500  496 S    0  0.0   0:00.00 getty

---

### Post by wolfen69 on 2011-12-15
Boot to a 64bit live cd (preferably a different one than you used to install with) and let us know what your memory now reads.

---

### Post by Ifaistos on 2011-12-16
I am sorry for troubling you guys.  It seems that the problem is elsewhere.

When I said that the Bios is detecting the memory correctly I was wrong... well partially.

In order for me to check if the memory was detected correctly I pressed F2 during boot, and went into the BIOS setup.  There I could clearly see that all 4 memory chips were correctly detected, and indeed memory is detected as 4GBs.

However I didn't notice that when I boot the system the memory detected is 3.2 GBs.  So it is not Linuxes problem it's my computers.  Bios problem.

I will just mention it here, but I don't expect an answer.  If someone can provide help that would be great.

My motherboard is an Asrock, the one shown in my signature.  I have the BIOS version 1.30 which according to their site, it is the latest.

I checked in the forums and it seems that more people have the same problem as me.  According to Asrock, all I have to do is go into BIOS > Advanced > Chipset Settings and then enable the memory remap feature.

The funny part of this that THERE IS NO MEMORY REMAP setting, anywhere in the BIOS !!! LOL :D

I don't know what to do right now.. but I will figure smt out.
In the meanwhile if anyone can provide a logical expanation or help, it would be greatly appreciated, if not, thank you guys anyway.  The Ubuntu community has always been the best!!

Thank you all.

---

