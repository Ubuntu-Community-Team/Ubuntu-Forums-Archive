---
title: "Problem with computer hiccups"
date: 2008-07-12
forum: General Help
---

### Post by yosubis on 2008-07-12
I just installed Ubuntu 8.04 64 bit on my new computer and every 5 seconds or so the computer hiccups. Most noticeable by the mouse pointer, freezing for a split second, as well as the keyboard. If the hiccups happen while typing, the typed character at the time of the hiccup never makes it on-screen. Also the screensaver hiccups at presumably the same intervals.

Any ideas on how to fix this?

---

### Post by yosubis on 2008-07-12
A little bump, since after only 6 hours this post made it to page 3

---

### Post by prshah on 2008-07-12
> **yosubis said:**
> I just installed Ubuntu 8.04 64 bit on my new computer and every 5 seconds or so the computer hiccups. 

I have the same problem every now and again (but on 32-bit), and a restart fixes it fine. If you've already restarted to no effect, maybe you can give us some more information as below:

a) What processor ```
cat /proc/cpuinfo
```
b) What power-scaling methods do you have and use?```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors 
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 
```
c) Does turning Compiz off make a difference?

It may help to glance through a similar thread at [http://ubuntuforums.org/showthread.php?t=803551](http://ubuntuforums.org/showthread.php?t=803551)

---

### Post by yosubis on 2008-07-12
a) Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz
b.1 (first cat))powersave userspace ondemand conservative performance
b.2 (second cat))ondemand
c) no

---

### Post by yosubis on 2008-07-13
Anyone... Any ideas? I really don't want to use windows...
by the way, I don't know if the two are connected, but every time before the login screen appears, there is a garbled image of the ubuntu loader and a lot of green lines for two seconds or so, and then the login screen appears. The same happens when I exit my session, a garbled background image with green lines and after about 2 seconds the ubuntu shutdown screen appears.

---

### Post by perlluver on 2008-07-13
Sounds like compiz or your video card.  Did you install the drivers for your video card?

---

### Post by yosubis on 2008-07-13
Compiz is off, and before installing drivers and after installing the drivers the hiccups occour.

---

### Post by perlluver on 2008-07-13
I personally never had good luck with the 64 bit version.  I always use the 32 bit version.  It really didn't offer me anything better than the 32 bit version.  I'm not sure what would be causing those problems, other than video.

---

### Post by yosubis on 2008-07-13
The same here, that is why I removed the 64 bit and installed the 32 bit version just a few hours ago, but I suffer the exact same problem.

---

### Post by prshah on 2008-07-13
> **yosubis said:**
> Anyone... Any ideas?
 every time before the login screen appears, there is a garbled image of the ubuntu loader and a lot of green lines for two seconds or so,


I have the same problem on various Intel chipset graphics cards, including _some_ 965GM and _some_ 945 chipsets. I've never faced a problem because of it though, and it's not always reproducible (ie, it's there on some machines, but not there on other identical machines. Also in some cases, when things were fine before, it suddenly appeared, and vice-versa). So I don't believe that's related.

Can you post the output of ```
top -b -n 1
```

---

### Post by yosubis on 2008-07-13
```

top - 09:00:48 up 41 min,  2 users,  load average: 0.43, 0.41, 0.47
Tasks: 109 total,   1 running, 108 sleeping,   0 stopped,   0 zombie
Cpu(s): 17.1%us,  1.4%sy,  0.1%ni, 80.5%id,  0.8%wa,  0.0%hi,  0.1%si,  0.0%st
Mem:   3631056k total,   834544k used,  2796512k free,    56192k buffers
Swap:  2441840k total,        0k used,  2441840k free,   452312k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5994 israel    20   0  259m 125m  26m S   12  3.5  13:38.40 firefox            
 5945 israel    20   0 25200  11m 8032 S    4  0.3   0:01.06 nm-applet          
 5568 root      20   0 63680  38m 6184 S    2  1.1   0:50.07 Xorg               
    1 root      20   0  2844 1692  544 S    0  0.0   0:00.98 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.30 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   46 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0          
   47 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1          
   50 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid             
   51 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify       
  139 root      15  -5     0    0    0 S    0  0.0   0:00.00 kseriod            
  181 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush            
  182 root      20   0     0    0    0 S    0  0.0   0:00.40 pdflush            
  183 root      15  -5     0    0    0 S    0  0.0   0:00.00 kswapd0            
  224 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0              
  225 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/1              
 1405 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd      
 1407 root      15  -5     0    0    0 S    0  0.0   0:00.00 khubd              
 1587 root      15  -5     0    0    0 S    0  0.0   0:00.10 ata/0              
 1615 root      15  -5     0    0    0 S    0  0.0   0:00.10 ata/1              
 1616 root      15  -5     0    0    0 S    0  0.0   0:00.00 ata_aux            
 2312 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_0          
 2314 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_1          
 2332 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_2          
 2333 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_3          
 2345 root      15  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_4          
 2346 root      15  -5     0    0    0 S    0  0.0   0:00.30 scsi_eh_5          
 2591 root      15  -5     0    0    0 S    0  0.0   0:00.00 reiserfs/0         
 2592 root      15  -5     0    0    0 S    0  0.0   0:00.00 reiserfs/1         
 2795 root      16  -4  2520 1040  380 S    0  0.0   0:00.16 udevd              
 3165 root      15  -5     0    0    0 S    0  0.0   0:00.00 kpsmoused          
 4741 root      20   0  1716  512  440 S    0  0.0   0:00.00 getty              
 4742 root      20   0  1716  508  440 S    0  0.0   0:00.00 getty              
 4744 root      20   0  1716  508  440 S    0  0.0   0:00.00 getty              
 4747 root      20   0  1716  512  440 S    0  0.0   0:00.00 getty              
 4748 root      20   0  1716  508  440 S    0  0.0   0:00.00 getty              
 4928 root      20   0  2456 1356  692 S    0  0.0   0:00.00 acpid              
 4965 root      15  -5     0    0    0 S    0  0.0   0:02.96 kondemand/0        
 4966 root      15  -5     0    0    0 S    0  0.0   0:02.74 kondemand/1        
 5049 syslog    20   0  1936  684  532 S    0  0.0   0:00.20 syslogd            
 5106 root      20   0  1872  536  444 S    0  0.0   0:00.10 dd                 
 5108 klog      20   0  3144 2040  424 S    0  0.1   0:00.16 klogd              
 5130 messageb  20   0  2972 1376  792 S    0  0.0   0:00.06 dbus-daemon        
 5146 root      20   0 21088 2120 1820 S    0  0.1   0:00.30 NetworkManager     
 5160 root      20   0  3536 1320 1132 S    0  0.0   0:00.00 NetworkManagerD    
 5173 root      20   0  4112 1112  908 S    0  0.0   0:00.00 system-tools-ba    
 5193 avahi     20   0  2760 1420 1208 S    0  0.0   0:00.02 avahi-daemon       
 5194 avahi     20   0  2760  464  288 S    0  0.0   0:00.00 avahi-daemon       
 5235 root      20   0  6048 2512 1900 S    0  0.1   0:00.00 cupsd              
 5301 root      20   0  2020  904  776 S    0  0.0   0:00.10 dhcdbd             
 5320 haldaemo  20   0  6308 4332 3576 S    0  0.1   0:00.32 hald               
 5323 root      20   0  8976 2368 1604 S    0  0.1   0:00.00 console-kit-dae    
 5385 root      20   0  3352 1168  984 S    0  0.0   0:00.00 hald-runner        
 5401 root      20   0  3428 1240 1088 S    0  0.0   0:00.00 hald-addon-cpuf    
 5402 haldaemo  20   0  2204  904  780 S    0  0.0   0:00.00 hald-addon-acpi    
 5404 root      20   0  3416 1160 1012 S    0  0.0   0:00.02 hald-addon-inpu    
 5434 root      20   0  3420 1156 1004 S    0  0.0   0:00.42 hald-addon-stor    
 5454 root      20   0  3172 1260 1092 S    0  0.0   0:00.00 hcid               
 5461 root      15  -5     0    0    0 S    0  0.0   0:00.00 btaddconn          
 5462 root      15  -5     0    0    0 S    0  0.0   0:00.00 btdelconn          
 5473 root      20   0  3020 1100  968 S    0  0.0   0:00.00 bluetoothd-serv    
 5474 root      20   0  3084 1296 1148 S    0  0.0   0:00.00 bluetoothd-serv    
 5479 root      10 -10     0    0    0 S    0  0.0   0:00.00 krfcommd           
 5562 root      20   0 14060 1604  976 S    0  0.0   0:00.00 gdm                
 5565 root      20   0 14516 2996 2220 S    0  0.1   0:00.00 gdm                
 5580 dhcp      20   0  2440 1184  868 S    0  0.0   0:00.10 dhclient           
 5617 daemon    20   0  1984  424  300 S    0  0.0   0:00.00 atd                
 5631 root      20   0  2104  884  712 S    0  0.0   0:00.00 cron               
 5711 root      20   0  1716  508  440 S    0  0.0   0:00.00 getty              
 5800 israel    20   0  7232 4292 1900 S    0  0.1   0:00.72 gconfd-2           
 5802 israel    20   0 14340 2044 1648 S    0  0.1   0:00.00 gnome-keyring-d    
 5803 israel    20   0 28860 7504 6300 S    0  0.2   0:00.06 x-session-manag    
 5856 israel    20   0 23056 6768 4848 S    0  0.2   0:00.06 seahorse-agent     
 5860 israel    20   0  2696 1128  772 S    0  0.0   0:00.12 dbus-daemon        
 5861 israel    20   0 40624 9896 7924 S    0  0.3   0:00.28 gnome-settings-    
 5867 israel    20   0 28484 5756 3312 S    0  0.2   0:00.48 pulseaudio         
 5872 israel    20   0  5776 2248 1836 S    0  0.1   0:00.00 gconf-helper       
 5885 israel    20   0 15216 2560 1688 S    0  0.1   0:01.12 gnome-screensav    
 5886 israel    20   0 20544  11m 7364 S    0  0.3   0:01.74 metacity           
 5887 israel    20   0 36376  20m  13m S    0  0.6   0:01.50 gnome-panel        
 5889 israel    20   0 75888  31m  14m S    0  0.9   0:02.73 nautilus           
 5896 israel    20   0 41112 3284 2444 S    0  0.1   0:00.10 bonobo-activati    
 5915 israel    20   0  5636 2360 1788 S    0  0.1   0:00.10 gvfsd              
 5920 israel    20   0 29048 1876 1488 S    0  0.1   0:00.00 gvfs-fuse-daemo    
 5925 israel    20   0 14728 5784 4876 S    0  0.2   0:00.02 bluetooth-apple    
 5928 israel    20   0 27180  14m 9508 S    0  0.4   0:00.14 update-notifier    
 5934 israel    20   0 28660 9544 7976 S    0  0.3   0:00.04 evolution-alarm    
 5935 israel    20   0 15216 5572 4712 S    0  0.2   0:00.02 tracker-applet     
 5937 israel    39  19 31504  10m 2288 S    0  0.3   0:00.04 trackerd           
 5941 israel    20   0 20672 4620 3420 S    0  0.1   0:00.00 gnome-volume-ma    
 5948 israel    20   0 24268  11m 7156 S    0  0.3   0:00.08 python             
 5950 israel    20   0 23068 7380 5536 S    0  0.2   0:00.06 gnome-power-man    
 5958 israel    20   0  5372 2124 1832 S    0  0.1   0:00.00 gvfsd-burn         
 5964 israel    20   0 23316 9.9m 7484 S    0  0.3   0:00.08 trashapplet        
 5968 israel    20   0 14864 2520 2144 S    0  0.1   0:00.00 gvfsd-trash        
 5980 israel    20   0 44352  14m 9648 S    0  0.4   0:00.13 mixer_applet2      
 5982 israel    20   0 26036  12m 8556 S    0  0.4   0:00.12 fast-user-switc    
 6403 israel    20   0 74840  19m  10m S    0  0.6   0:00.20 gnome-terminal     
 6406 israel    20   0  2912  856  708 S    0  0.0   0:00.00 gnome-pty-helpe    
 6407 israel    20   0  5628 3044 1412 S    0  0.1   0:00.06 bash               
 6424 israel    20   0  2304 1000  756 R    0  0.0   0:00.00 top

```

---

### Post by yosubis on 2008-07-13
and apparently 3d screensaver never leave. If a 3d screensaver kicks in and I move the mouse to leave, The screen remains with the screensaver's last state and a movable mouse cursor, the cursor will change if I'll move it over a text box or off a text box.

---

### Post by yosubis on 2008-07-13
any ideas? thoughts? suggestions?

---

### Post by yosubis on 2008-07-13
Well, I assume no one knows whats wrong... Thanks anyway.

---

### Post by yosubis on 2008-07-13
Ok, new info... I have 2 ethernet cards, one is not connected. In the System log viewer it says:

"[  XXX.XXXXXX] eth0: Tx timeout - resetting"

and it says that about every 2 seconds.

For now, I don't need it. How can I disable it, without taking it out?

Edit: forgot to mention the X's represent numbers

---

### Post by prshah on 2008-07-13
> **yosubis said:**
> Ok, new info... I have 2 ethernet cards, one is not connected. 
 How can I disable it, without taking it out?

```
sudo ifdown eth0
``` For a more permanent solution, you can comment out the lines related to eth0 in your '/etc/network/interfaces' file.

---

