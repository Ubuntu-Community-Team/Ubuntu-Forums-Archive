---
title: "Xorg app using 200mb !?"
date: 2008-08-27
forum: General Help
---

### Post by ikus060 on 2008-08-27
```
Hi,

I'm using Ubuntu 7.10 and I notice this last week that my computer is slow. It's not a bomb but it's have enough power to do what I need. I notice that my memory usage are very high. Usually I get at this point by not restarting by computer for more than a month. Now, in one day the my computer use the swap! Usually it's never happen!

Here the output of top :

top - 21:24:16 up 3 days, 10:08,  4 users,  load average: 0.40, 0.49, 0.62
Tasks: 146 total,   3 running, 143 sleeping,   0 stopped,   0 zombie
Cpu(s):  4.6%us,  1.3%sy,  0.0%ni, 93.4%id,  0.0%wa,  0.0%hi,  0.7%si,  0.0%st
Mem:   2075996k total,  2015208k used,    60788k free,    19272k buffers
Swap:  2000084k total,  1000200k used,   999884k free,   725744k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                
 5661 root      16   0  977m 605m 480m R  2.0 29.9  30:27.13 Xorg                                                                                   
 4324 patapouf   5 -10  360m 293m 285m S  0.0 14.5   1:09.91 vmware-vmx                                                                             
 9674 patapouf  15   0 1198m 210m  22m S  0.0 10.4  31:24.41 eclipse                                                                                
23691 patapouf  15   0  111m  77m 7716 S  2.6  3.8 113:59.33 transmission                                                                           
 4926 patapouf  15   0  203m  74m  23m S  1.3  3.7   1:17.67 firefox-bin                                                                            
 6221 patapouf  15   0  217m  64m  18m S  0.0  3.2   4:01.54 thunderbird-bin                                                                        
 2456 patapouf  15   0  121m  43m  11m S  0.0  2.1   0:37.18 evince                                                                                 
 4312 patapouf  15   0 67564  33m  17m S  0.0  1.6   0:04.87 vmware                                                                                 
 7037 patapouf  15   0  122m  33m  14m S  0.0  1.6  28:47.83 rhythmbox                                                                              
 6011 patapouf  15   0  103m  31m  17m S  0.0  1.5   0:24.87 nautilus                                                                               
 6010 patapouf  18   0 87500  20m  11m S  0.0  1.0   1:45.95 gnome-panel                                                                            
 6036 patapouf  15   0 69072  15m  11m S  0.0  0.7   0:06.28 pidgin                                                                                 
 6154 patapouf  15   0 82496  13m 9628 S  0.0  0.7   0:09.12 python                                                                                 
 6150 patapouf  18   0 75404  13m 8696 S  0.0  0.7   0:11.67 deskbar-applet                                                                         
 7109 patapouf  16   0 63500  12m 8968 R  0.0  0.6   0:06.13 gnome-terminal                                                                         
 6044 patapouf  15   0 63600  10m 9064 S  0.0  0.5   0:07.45 tomboy                                                                                 
11773 patapouf  18   0 36368  10m 7460 S  0.0  0.5   0:06.25 notification-da                                                                        
 6152 patapouf  15   0 70580 9880 8460 S  0.0  0.5   0:00.75 gweather-applet                                                                        
 6007 patapouf  15   0 18876 9828 7996 S  0.0  0.5   1:38.14 metacity                                                                               
 6031 patapouf  21   0 38880 9804 8400 S  0.0  0.5   0:00.86 update-notifier                                                                        
 6223 patapouf  15   0 54316 9736 8576 S  0.0  0.5   0:00.28 mixer_applet2                                                                          
 6001 patapouf  19   0 53004 9208 7948 S  0.0  0.4   0:10.15 gnome-settings-                                                                        
 6063 patapouf  15   0 45952 7812 6980 S  0.0  0.4   0:03.78 nm-applet                                                                              
 6156 patapouf  15   0 67220 7588 6600 S  0.0  0.4   0:00.21 trashapplet                                                                            
 6047 patapouf  15   0 18364 7048 6200 S  0.0  0.3   0:03.02 alltray                                                                                
 6042 patapouf  15   0 68172 6892 6144 S  0.0  0.3   0:00.10 evolution-alarm                                                                        
 6087 patapouf  15   0 36664 6144 5552 S  0.0  0.3   0:00.05 evolution-excha                                                                        
 6067 patapouf  15   0 22852 5888 5152 S  0.0  0.3   0:00.43 gnome-power-man                                                                        
 5954 patapouf  15   0 28084 5840 5392 S  0.0  0.3   0:00.09 x-session-manag                                                                        
 6060 patapouf  15   0 23012 5664 4960 S  0.0  0.3   0:01.00 python                                                                                 
 6025 patapouf  15   0 19564 5396 5004 S  0.0  0.3   0:00.03 vino-session                                                                           
 6070 patapouf  15   0 19016 5200 4596 S  0.0  0.3   1:21.25 gnome-screensav                                                                        
 6026 patapouf  15   0 13624 5084 4688 S  0.0  0.2   0:00.08 bluetooth-apple                                                                        
 6015 patapouf  15   0 19684 4192 3732 S  0.0  0.2   0:00.64 gnome-volume-ma                                                                        
 5796 root      15   0 16912 4040 1704 S  0.0  0.2   0:03.46 vmware-serverd                                                                         
 6715 patapouf  15   0  6052 3400 1424 S  0.0  0.2   0:00.13 bash                                                                                   
 5996 patapouf  18   0  7132 3360 1864 S  0.0  0.2   0:01.29 gconfd-2                                                                               
 6091 patapouf  15   0 66440 3212 2976 S  0.0  0.2   0:00.04 evolution-data-                                                                        
 6024 patapouf  15   0  8756 2840 2648 S  0.0  0.1   0:00.05 gnome-vfs-daemo                                                                        
 5138 root      15   0  6312 2780 1220 S  0.0  0.1   0:03.68 ddclient                                                                               
 6020 patapouf  15   0 39996 2772 2196 S  0.0  0.1   0:00.15 bonobo-activati                                                                        

```

I notice that Xorg use alot of memory Virtual ans share. I compare it with my laptop (ubuntu 8.04) and there is big difference.

As describe in top logs, I have 2Gig of ram.

So, without giving me a solution, do you find it normal and do you have a similar situation ?

Thanks for comment/help.

---

### Post by mb_webguy on 2008-08-27
This issue seems to be cropping up fairly often lately.  Several people have reported that Xorg is using an inordinately large amount of system resources -- usually CPU cycles, but memory as well.  Unfortunately, I haven't read anything about possible causes or solutions...

Are you using advanced Compiz settings or Emerald, by any chance?

---

### Post by ikus060 on 2008-08-28
Hi mb_webguy,

Thanks for your reply. Great that I'm not the only person having this problem! I'm not alone anymore.

My graphics setup is a DualScreen 1280*1024. I'm using Metacity, so there is not 3D effect.

---

