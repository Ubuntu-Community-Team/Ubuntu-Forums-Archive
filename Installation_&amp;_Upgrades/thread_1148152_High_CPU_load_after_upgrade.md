---
title: "High CPU load after upgrade"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by Jeje on 2009-05-04
After upgrading to ubuntu 9.04 from 8.10 the CPU load stays at around 60% in the system monitor & the fan is quite noisy. I can't identify the responsible process - there is no process with excessive CPU usage in the process list!?

```
top - 09:04:05 up 6 min,  2 users,  load average: 1.98, 1.72, 0.81
Tasks: 140 total,   4 running, 136 sleeping,   0 stopped,   0 zombie
Cpu(s): 36.5%us, 19.8%sy,  0.0%ni, 43.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1026036k total,   524400k used,   501636k free,    39328k buffers
Swap:  2931852k total,        0k used,  2931852k free,   244412k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 3054 root      20   0  346m  15m 7768 S    8  1.5   0:32.85 Xorg               
 3505 el4       20   0  3056 1244  652 S    8  0.1   0:22.37 dbus-daemon        
 3340 el4       20   0 26340 7144 5604 S    5  0.7   0:17.02 gnome-session      
 3513 el4       20   0  8108 4984 2184 S    4  0.5   0:11.27 gconfd-2           
 3875 el4       20   0 22452 9144 7292 S    3  0.9   0:07.98 indicator-apple    
 3647 el4       20   0 50416  19m  13m S    2  1.9   0:06.36 gnome-panel        
 3536 el4       20   0 29864 9576 6664 S    1  0.9   0:06.44 gnome-settings-    
 3665 el4       20   0 27900  13m 8036 S    1  1.4   0:05.02 python             
 7925 el4       20   0 39104  14m 9460 R    1  1.4   0:02.36 gnome-terminal     
 3693 el4       20   0 17584 6000 4920 S    1  0.6   0:01.41 notification-da    
 3657 el4       20   0 33108  13m  10m S    1  1.4   0:02.01 update-notifier    
 3676 el4       20   0 16024 6488 5356 S    1  0.6   0:01.36 bluetooth-apple    
 3677 el4       20   0 33992  11m 8792 S    1  1.2   0:01.83 nm-applet          
 4412 el4       20   0 16424 2564 1412 S    1  0.2   0:03.98 gnome-screensav    
 9503 el4       20   0  2452 1188  908 R    1  0.1   0:00.04 top                
 3656 el4       20   0 18016 4172 2876 S    0  0.4   0:01.63 xfce4-settings-    
 3680 el4       20   0 25096 9164 6312 S    0  0.9   0:02.36 gnome-power-man    
 5873 el4       20   0  145m  54m  22m S    0  5.4   0:18.85 firefox            
 9563 el4       20   0 20232 3416 2476 R    0  0.3   0:00.01 vino-server        
    1 root      20   0  3084 1888  564 S    0  0.2   0:01.34 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.01 migration/0        
    4 root      15  -5     0    0    0 R    0  0.0   0:00.23 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.02 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.24 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.01 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   12 root      RT  -5     0    0    0 S    0  0.0   0:00.00 kstop/0            
   13 root      RT  -5     0    0    0 S    0  0.0   0:00.00 kstop/1            
   14 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/0      
   15 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/1      
   16 root      15  -5     0    0    0 S    0  0.0   0:00.03 kblockd/0          
   17 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1          
   18 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid             
   19 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify       
   20 root      15  -5     0    0    0 S    0  0.0   0:00.00 cqueue             
   21 root      15  -5     0    0    0 S    0  0.0   0:00.03 ata/0              
   22 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata/1              
   23 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata_aux            
   24 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd      
   25 root      15  -5     0    0    0 S    0  0.0   0:00.00 khubd              
   26 root      15  -5     0    0    0 S    0  0.0   0:00.01 kseriod            
   27 root      15  -5     0    0    0 S    0  0.0   0:00.00 kmmcd              
   28 root      15  -5     0    0    0 S    0  0.0   0:00.00 btaddconn          
   29 root      15  -5     0    0    0 S    0  0.0   0:00.00 btdelconn          
   30 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush            
   31 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush            
   32 root      15  -5     0    0    0 S    0  0.0   0:00.00 kswapd0            
   33 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0              
   34 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/1              
   35 root      15  -5     0    0    0 S    0  0.0   0:00.00 ecryptfs-kthrea    
   38 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_0          
   39 root      15  -5     0    0    0 S    0  0.0   0:00.03 scsi_eh_1          
   40 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_2          
   41 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_3          
   42 root      15  -5     0    0    0 S    0  0.0   0:00.00 kstriped           
   43 root      15  -5     0    0    0 S    0  0.0   0:00.00 kmpathd/0          
   44 root      15  -5     0    0    0 S    0  0.0   0:00.00 kmpathd/1          
   45 root      15  -5     0    0    0 S    0  0.0   0:00.00 kmpath_handlerd    
   46 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksnapd             
   47 root      15  -5     0    0    0 S    0  0.0   0:00.00 kondemand/0        
   48 root      15  -5     0    0    0 S    0  0.0   0:00.00 kondemand/1        
   49 root      10 -10     0    0    0 S    0  0.0   0:00.00 krfcommd           
  657 root      15  -5     0    0    0 S    0  0.0   0:00.06 kjournald          
  790 root      16  -4  2224  572  316 S    0  0.1   0:00.19 udevd              
 1374 root      15  -5     0    0    0 S    0  0.0   0:00.00 edac-poller        
 1380 root      15  -5     0    0    0 S    0  0.0   0:00.00 kpsmoused          
 1735 root      15  -5     0    0    0 S    0  0.0   0:00.00 kjournald          
 1739 root      20   0  3976 1004  600 S    0  0.1   0:00.00 mount.ntfs         
 2033 root      20   0  1808  532  460 S    0  0.1   0:00.00 getty              
 2034 root      20   0  1808  528  460 S    0  0.1   0:00.00 getty              
 2037 root      20   0  1808  532  460 S    0  0.1   0:00.00 getty              
 2038 root      20   0  1808  532  460 S    0  0.1   0:00.00 getty              
 2039 root      20   0  1808  532  460 S    0  0.1   0:00.00 getty              
 2107 root      20   0  2204 1092  556 S    0  0.1   0:00.00 acpid              
 2174 syslog    20   0  2040  684  540 S    0  0.1   0:00.04 syslogd            
 2192 root      20   0  1968  536  440 S    0  0.1   0:00.09 dd                 
 2194 klog      20   0  3632 2412  444 S    0  0.2   0:00.14 klogd              
 2212 messageb  20   0  3012 1392  832 S    0  0.1   0:00.25 dbus-daemon        
 2231 root      20   0  5436 1040  652 S    0  0.1   0:00.00 sshd               
 2283 root      20   0  2140  488  412 S    0  0.0   0:00.00 vmnet-bridge       
 2801 root      20   0  2652  400  256 S    0  0.0   0:00.00 vmnet-dhcpd        
 2806 root      20   0  2116  296  232 S    0  0.0   0:00.00 vmnet-netifup      
 2811 root      20   0  2652  408  256 S    0  0.0   0:00.00 vmnet-dhcpd        
 2813 root      20   0  2592  592  492 S    0  0.1   0:00.00 vmnet-natd         
 2818 root      20   0  2116  296  232 S    0  0.0   0:00.00 vmnet-netifup      
 2858 root      20   0 10584 1444  896 S    0  0.1   0:00.00 winbindd           
 2862 root      20   0 10584 1196  648 S    0  0.1   0:00.00 winbindd           
 2879 haldaemo  20   0  6692 4420 3616 S    0  0.4   0:00.30 hald               
 2882 root      20   0 17380 2576 1784 S    0  0.3   0:00.03 console-kit-dae    
 2945 root      20   0  3328 1120  916 S    0  0.1   0:00.01 hald-runner        
 2974 root      20   0  5176 1784 1576 S    0  0.2   0:00.00 hald-addon-inpu    
 3018 root      20   0  5180 1804 1592 S    0  0.2   0:00.07 hald-addon-stor    
 3020 haldaemo  20   0  5032 1760 1540 S    0  0.2   0:00.00 hald-addon-acpi    
 3021 root      20   0  5180 1800 1588 S    0  0.2   0:00.00 hald-addon-stor    
 3039 root      20   0 15028 2012 1260 S    0  0.2   0:00.00 gdm                
 3041 root      20   0 15664 3424 2448 S    0  0.3   0:00.25 gdm                
 3061 root      20   0 16420 2692 2196 S    0  0.3   0:00.05 NetworkManager     
 3076 root      20   0  4276 1336 1108 S    0  0.1   0:00.01 wpa_supplicant     
 3078 root      20   0  7048 3128 2592 S    0  0.3   0:00.01 nm-system-setti    
 3082 avahi     20   0  3076 1536 1268 S    0  0.1   0:00.04 avahi-daemon       
 3083 avahi     20   0  2944  512  300 S    0  0.0   0:00.00 avahi-daemon       
 3104 root      20   0  6236 2464 1764 S    0  0.2   0:00.02 cupsd              
 3151 root      20   0  4324 1164  932 S    0  0.1   0:00.00 system-tools-ba    
 3215 daemon    20   0  2096  452  324 S    0  0.0   0:00.00 atd                
 3240 root      20   0  3480 1032  824 S    0  0.1   0:00.01 cron               
 3318 root      20   0  1808  524  460 S    0  0.1   0:00.00 getty              
 3494 root      20   0  2276  996  868 S    0  0.1   0:00.00 dhclient           
 3501 el4       20   0  4784  604  288 S    0  0.1   0:00.00 ssh-agent          
 3504 el4       20   0  3144  692  456 S    0  0.1   0:00.00 dbus-launch        
 3510 el4       20   0 94616 5296 3972 S    0  0.5   0:00.20 pulseaudio         
 3511 el4       20   0  7844 2628 2120 S    0  0.3   0:00.00 gconf-helper       
 3525 el4       20   0 18960 6044 4340 S    0  0.6   0:00.11 seahorse-agent     
 3529 el4       20   0  5616 2120 1800 S    0  0.2   0:01.02 gvfsd              
 3560 el4       20   0 25644 2312 1740 S    0  0.2   0:00.09 gnome-keyring-d    
 3588 root      15  -5     0    0    0 S    0  0.0   0:00.00 cifsoplockd        
 3591 root      15  -5     0    0    0 S    0  0.0   0:00.00 cifsdnotifyd       
 3595 root      15  -5     0    0    0 S    0  0.0   0:00.00 cifsd              
 3601 root      15  -5     0    0    0 S    0  0.0   0:00.00 cifsd              
 3646 el4       20   0 19096 9.8m 8004 S    0  1.0   0:01.62 metacity           
 3648 el4       20   0 87312  19m  13m S    0  2.0   0:02.33 nautilus           
 3650 el4       20   0 41780 3468 2672 S    0  0.3   0:00.18 bonobo-activati    
 3675 el4       20   0 22732 8476 6776 S    0  0.8   0:04.57 vino-server        
 3682 el4       20   0  3664 1816 1556 S    0  0.2   0:00.11 xfconfd            
 3730 ntp       20   0  4348 1336 1016 S    0  0.1   0:00.00 ntpd               
 3732 el4       20   0 28896 9904 7424 S    0  1.0   0:00.17 trashapplet        
 3736 el4       20   0  5940 2728 2332 S    0  0.3   0:00.05 gvfsd-trash        
 3808 el4       20   0  7844 3504 2784 S    0  0.3   0:00.03 gvfs-hal-volume    
 3813 el4       20   0  8220 3076 2336 S    0  0.3   0:00.01 gvfs-gphoto2-vo    
 3851 el4       20   0  164m  39m  18m S    0  3.9   0:01.89 dropbox            
 3865 el4       20   0 28940 9840 7400 S    0  1.0   0:00.18 vinagre-applet     
 4001 el4       20   0  5616 2224 1920 S    0  0.2   0:00.00 gvfsd-burn         
 5558 el4       20   0  1872  552  472 S    0  0.1   0:00.00 thunderbird        
 5571 el4       20   0  1872  548  464 S    0  0.1   0:00.00 run-mozilla.sh     
 5576 el4       20   0  137m  43m  21m S    0  4.3   0:07.10 thunderbird-bin    
 7940 el4       20   0  2036  700  580 S    0  0.1   0:00.00 gnome-pty-helpe    
 7943 el4       20   0  6660 3916 1456 S    0  0.4   0:00.26 bash               

```

Any idea anybody? Thanks,
Daniel

---

### Post by fjpos on 2009-05-04
Hi Jeje,


I have exaclty the same problem and in fact your process dump looks exacly like mine CPU always around 36%. Nothing appears to be causing it. It is a X11 or GDM problem though because when you close gdm it goes back to normal (CPU 2%).

I upgdraded from 8.10 to 9.04 which went 98%, tracker had some problems which I have now turned off.

Patrick

---

### Post by fjpos on 2009-05-04
Hi gain Jeje and other too high CPU Xorg ers.

After trying to close down a few services to perhaps see what  if anything I was using was overusing Xorg I eventually [COLOR="Red"]stopped vino-server[/COLOR] which in itself was not using a lot of the  CPU. However straight after I killed it bang my CPU usage went down 1%-4%. Vino-server is part of the gnome remote desktop. The system still did feel a little highly strung with the CPU happy to increase  with  compiz usage  which I have somewhat turned of some it's features. Note before I upgraded  all worked fine under 8.10. However 9.04 is now a how lot better as expected.  I hope this may help

---

### Post by Jeje on 2009-05-05
Hi fjpos

Thanks for that tip! Issueing a 'killall vino-server' does the job. Even though it is respawn straight away the CPU load stays low?!

---

