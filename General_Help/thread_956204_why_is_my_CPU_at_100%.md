---
title: "why is my CPU at 100%???"
date: 2008-10-23
forum: General Help
---

### Post by a_sad_snowman on 2008-10-23
i installed ubuntu 8.04 LTS on my HP Pavilion a305w yesterday. I haven't installed anything extra yet, but my cpu usage goes between the high 90's and 100% even when its idling. needless to say, its very very slow, it took several attempts to even manage to post this. is there anything i can do to fix this? i'm fairly new to linux, so go easy on the terms please! any input is appreciated.


top - 00:35:06 up 1 day,  1:27,  2 users,  load average: 3.67, 3.42, 3.35
Tasks: 107 total,   2 running, 104 sleeping,   0 stopped,   1 zombie
Cpu(s): 21.3%us, 78.4%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:    766636k total,   757676k used,     8960k free,     7712k buffers
Swap:   786424k total,    39772k used,   746652k free,   405220k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
   45 root      15  -5     0    0    0 R 57.7  0.0 341:41.36 kacpi_notify       
 4673 root      20   0  2456 1432  692 S  9.0  0.2  47:51.27 acpid              
 4786 syslog    20   0  1936  680  532 S  7.0  0.1  34:04.81 syslogd            
 5063 haldaemo  20   0  6152 4164 3560 S  6.3  0.5  33:34.85 hald               
 4839 root      20   0  1872  532  444 S  4.6  0.1  24:34.15 dd                 
 5147 haldaemo  20   0  2204  956  824 S  4.3  0.1  23:58.29 hald-addon-acpi    
 5332 root      20   0  240m  26m 9616 S  4.3  3.5  20:54.11 Xorg               
18954 adam      20   0  140m  52m  20m S  3.3  7.0   0:33.37 firefox            
 4841 klog      20   0  3256 2096  424 S  2.7  0.3  13:06.88 klogd              
 1488 root      15  -5     0    0    0 S  0.7  0.0   0:18.48 scsi_eh_1          
 7213 root      15  -5     0    0    0 S  0.7  0.0   0:31.14 rt73usb            
18932 adam      20   0 94276  21m  11m S  0.7  2.9   0:03.24 gnome-terminal     
18972 adam      20   0  2308 1104  852 R  0.7  0.1   0:00.04 top                
 5803 adam      20   0 49544  15m  11m S  0.3  2.0   0:43.04 nm-applet          
    1 root      20   0  2844 1692  544 S  0.0  0.2   0:01.40 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0

---

### Post by wfp on 2008-10-23
I did a search for you on launchpad and it seems like there have been a few people suffering from a bug that set's the high cpu > 45 root 15 -5 0 0 0 R 57.7 0.0 341:41.36 kacpi_notify.  Most of these people were having problems on there laptops thou. From what i read sounds like there is a fix in Intrepid, which you can dowload in 8 days. I am pretty new to linux so maybe some one with more knowledge can help you.

---

### Post by ricardisimo on 2008-10-23
Mine is through the roof today as well, and I suspect it has something to do with my wireless connection, which is normally spotless, but today I had to tinker with it a bit. I think they discuss a similar problem in [this thread]("http://ubuntuforums.org/showthread.php?t=949321"), but I didn't read the whole thing. Try shutting down your wifi for a bit to see if that's it for you also.

So, in the meantime, what do I do about this? Anything? So far as I can tell, the someone bumped the transceiver for the coffeeshop's signal next door, and now I'm getting a substantially weaker signal. But I don't understand why my CPU is working so much harder. Also, when I go to check out the processes in System Monitor, everything running adds up to the usual 10-15%. Where is the ghost-usage coming from?

---

### Post by ricardisimo on 2008-10-23
Hmmm... I just basically rebooted the wireless by trying to connect to a password-protected network (and then just hit "Cancel") and my wifi defaulted back to the last one that worked, and now all is well and good in my CPU World again. If anything changes, I'll report back.

---

