---
title: "Fresh install extremely slow on HP dv6113"
date: 2008-10-02
forum: General Help
---

### Post by erinspice on 2008-10-02
I don't think this problem is specific to my laptop, so I'm putting it in this forum.

I installed Ubuntu on my HP dv6113 about 6 weeks ago. I previously used FC8.  I have found that my laptop runs much more slowly now. My server load is frequently 5-10 with only a few apps running.  I almost always have Firefox, Thunderbird, Pidgin, and a terminal with an ssh session open, which is the same as when I used FC8.  Occasionally I run ktorrent and picasa.  What can I change or check to figure out why it's running so much more slowly than FC8 did and to fix it?

top output:

```
top - 11:40:09 up 17 days, 20:40,  9 users,  load average: 5.67, 3.55, 2.20
Tasks: 147 total,   2 running, 145 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.6%us,  1.5%sy,  0.0%ni, 22.4%id, 73.9%wa,  0.0%hi,  0.6%si,  0.0%st
Mem:    995780k total,   987720k used,     8060k free,      464k buffers
Swap:  1052248k total,   772620k used,   279628k free,    41808k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                                                 
24530 erin      20   0  877m 264m  13m D    3 27.2 290:37.01 firefox                                                                                                                                 
 5661 root      20   0  241m  95m 4524 S    1  9.8 434:40.45 Xorg                                                                                                                                    
 5575 root      15  -5     0    0    0 S    1  0.0  89:41.92 ipolldevd                                                                                                                               
 9498 erin      20   0  736m 142m  14m R    1 14.6  12:17.07 thunderbird-bin                                                                                                                         
 6408 erin      20   0  750m  82m 5560 S    1  8.5  61:49.45 pidgin                                                                                                                                  
11848 erin      20   0 18992 1296  932 R    1  0.1   0:00.08 top                                                                                                                                     
20864 erin      20   0 45768 1012  820 S    1  0.1   0:20.58 ssh                                                                                                                                     
24580 erin      20   0  240m 9440 4080 S    1  0.9   6:13.58 gnome-terminal                                                                                                                          
  203 root      15  -5     0    0    0 D    0  0.0   4:13.04 kswapd0                                                                                                                                 
 5074 root      15  -5     0    0    0 S    0  0.0  15:33.75 kondemand/0                                                                                                                             
 6214 erin      20   0  216m 1596 1280 S    0  0.2  67:39.15 pulseaudio                                                                                                                              
18373 erin      20   0  367m  27m 4480 S    0  2.8 256:11.30 ktorrent                                                                                                                                
21120 root      20   0 27740 1832 1108 S    0  0.2   1:13.39 openvpn                                                                                                                                 
25984 erin      20   0 45764  860  696 S    0  0.1  43:38.92 ssh                                                                                                                                     
    1 root      20   0  4020  420  368 S    0  0.0   0:01.20 init                                                                                                                                    
    2 root      15  -5     0    0    0 S    0  0.0   0:00.04 kthreadd                                                                                                                                
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.20 migration/0                                                                                                                             
    4 root      15  -5     0    0    0 S    0  0.0   0:00.24 ksoftirqd/0                                                                                                                             
    5 root      RT  -5     0    0    0 S    0  0.0   0:01.12 watchdog/0                                                                                                                              
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.26 migration/1                                                                                                                             
    7 root      15  -5     0    0    0 S    0  0.0   0:00.52 ksoftirqd/1                                                                                                                             
    8 root      RT  -5     0    0    0 S    0  0.0   0:01.20 watchdog/1                                                                                                                              
    9 root      15  -5     0    0    0 S    0  0.0   0:07.42 events/0                                                                                                                                
   10 root      15  -5     0    0    0 S    0  0.0   0:21.42 events/1                                                                                                                                
   11 root      15  -5     0    0    0 S    0  0.0   0:01.00 khelper                                                                                                                                 
   44 root      15  -5     0    0    0 S    0  0.0   0:02.90 kblockd/0                                                                                                                               
   45 root      15  -5     0    0    0 S    0  0.0   0:14.62 kblockd/1                                                                                                                               
   48 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid                                                                                                                                  
   49 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                                                                                                            
  151 root      15  -5     0    0    0 S    0  0.0   0:00.06 kseriod                                                                                                                                 
  246 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0                                                                                                                                   
  247 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/1                                                                                                                                   
 1541 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd                                                                                                                           
 1543 root      15  -5     0    0    0 S    0  0.0   0:00.00 khubd                                                                                                                                   
 1598 root      15  -5     0    0    0 S    0  0.0   0:02.24 ata/0                                                                                                                                   
 1609 root      15  -5     0    0    0 S    0  0.0   0:57.07 ata/1                                                                                                                                   
 1611 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata_aux                                                                                                                                 
 2236 erin      20   0  288m 1196 1196 S    0  0.1   0:00.49 evolution-data-                                                                                                                         
 2285 erin      20   0  286m 2340 2024 S    0  0.2   0:00.21 evolution-excha                                                                                                                         
 2322 root      15  -5     0    0    0 S    0  0.0   1:46.84 scsi_eh_0                                                                                                                               
 2328 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_1                                                                                                                               
 2352 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_2                                                                                                                               
 2355 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_3                                                                                                                               
 2621 root      15  -5     0    0    0 D    0  0.0   2:23.27 kjournald                                                                                                                               
 2820 root      16  -4 17188  428  348 S    0  0.0   1:28.20 udevd                                                                                                                                   
 3157 root      15  -5     0    0    0 S    0  0.0   0:00.00 kpsmoused                                                                                                                               
 3449 root      15  -5     0    0    0 S    0  0.0   0:00.00 b43                                                                                                                                     
 4323 root      15  -5     0    0    0 S    0  0.0   0:00.00 ntos_wq                                                                                                                                 
 4324 root      15  -5     0    0    0 S    0  0.0   0:00.00 ndis_wq                                                                                                                                 

```

free output:

```
             total       used       free     shared    buffers     cached
Mem:           972        963          8          0          3         51
-/+ buffers/cache:        907         64
Swap:         1027        701        326

```

rc3.d:
```
lrwxrwxrwx 1 root root  19 2008-08-25 09:59 S01policykit -> ../init.d/policykit
lrwxrwxrwx 1 root root  17 2008-08-25 09:59 S05vbesave -> ../init.d/vbesave
lrwxrwxrwx 1 root root  15 2008-08-25 09:59 S10acpid -> ../init.d/acpid
lrwxrwxrwx 1 root root  18 2008-08-25 09:59 S10sysklogd -> ../init.d/sysklogd
lrwxrwxrwx 1 root root  34 2008-08-25 09:59 S10xserver-xorg-input-wacom -> ../init.d/xserver-xorg-input-wacom
lrwxrwxrwx 1 root root  15 2008-08-25 09:59 S11klogd -> ../init.d/klogd
lrwxrwxrwx 1 root root  14 2008-08-25 09:59 S12dbus -> ../init.d/dbus
lrwxrwxrwx 1 root root  17 2008-08-26 13:19 S16openvpn -> ../init.d/openvpn
lrwxrwxrwx 1 root root  13 2008-09-18 15:19 S16ssh -> ../init.d/ssh
lrwxrwxrwx 1 root root  22 2008-08-25 09:59 S18avahi-daemon -> ../init.d/avahi-daemon
lrwxrwxrwx 1 root root  16 2008-08-25 09:59 S20apport -> ../init.d/apport
lrwxrwxrwx 1 root root  16 2008-08-25 09:59 S20cupsys -> ../init.d/cupsys
lrwxrwxrwx 1 root root  22 2008-08-25 09:59 S20hotkey-setup -> ../init.d/hotkey-setup
lrwxrwxrwx 1 root root  23 2008-08-25 09:59 S20nvidia-kernel -> ../init.d/nvidia-kernel
lrwxrwxrwx 1 root root  19 2008-08-25 09:59 S20powernowd -> ../init.d/powernowd
lrwxrwxrwx 1 root root  15 2008-08-25 09:59 S20rsync -> ../init.d/rsync
lrwxrwxrwx 1 root root  16 2008-08-25 09:59 S24dhcdbd -> ../init.d/dhcdbd
lrwxrwxrwx 1 root root  13 2008-08-25 09:59 S24hal -> ../init.d/hal
lrwxrwxrwx 1 root root  19 2008-08-25 09:59 S25bluetooth -> ../init.d/bluetooth
lrwxrwxrwx 1 root root  20 2008-08-25 09:59 S25pulseaudio -> ../init.d/pulseaudio
lrwxrwxrwx 1 root root  13 2008-08-25 09:59 S30gdm -> ../init.d/gdm
lrwxrwxrwx 1 root root  17 2008-08-25 09:59 S89anacron -> ../init.d/anacron
lrwxrwxrwx 1 root root  13 2008-08-25 09:59 S89atd -> ../init.d/atd
lrwxrwxrwx 1 root root  14 2008-08-25 09:59 S89cron -> ../init.d/cron
lrwxrwxrwx 1 root root  17 2008-08-25 09:59 S98usplash -> ../init.d/usplash
lrwxrwxrwx 1 root root  22 2008-08-25 09:59 S99acpi-support -> ../init.d/acpi-support
lrwxrwxrwx 1 root root  21 2008-08-25 09:59 S99laptop-mode -> ../init.d/laptop-mode
lrwxrwxrwx 1 root root  18 2008-08-25 09:59 S99rc.local -> ../init.d/rc.local
lrwxrwxrwx 1 root root  19 2008-08-25 09:59 S99rmnologin -> ../init.d/rmnologin

```

---

### Post by erinspice on 2008-10-05
Please excuse the shameless bump, but I really need to find a solution to this. My dual 1.6 Ghz processor laptop with 1GB RAM is almost unusable. I am going back to Fedora if I can't find a solution to this problem.

---

### Post by erinspice on 2009-05-03
Please excuse the ancient thread bump. I wanted to resolve this thread with the hope that it might help someone else. Passing the kernel the "noapic" option solved all my problems.

---

