---
title: "System using 100% of resources"
date: 2016-09-26
forum: Hardware
---

### Post by Gnusboy on 2016-09-26
Hey all
For the last several days, my system resources has been bouncing up and down, but mostly using 100% of resources on all four cpu.- even when there is no load, or a just 1 FireFox or window open or the file manager running.I don't know how to fix this.
When I check the system monitor, the graph shows a nearly constant draw, but the the processes do  not show what percent the CPU is using. This problem has made my system incredibly slow and browser windows and Libre Office will hang up - sometimes for as long as a minute or more. When I type, it can take a few seconds before the letters show on the screen. 
What can cause a system to act this way? At the moment, I'm showing the only apps running are Firefox (using 26% to 30% of the CPU) This Ubuntu window, the system monitor and the network tool are all the processes runnig. Everything else shows sleeping . I just now see the XORG is going on and off periodically. I don't know what that means.

When I ping Ubuntu.com it shows that time lag is 204 + miliseconds to connect. I don't recall ever seeing a lag like that in the past. It seems like that is very slow too.

My system is a bit older, but it's an AMD Phenom quad 9250 black,with 4 GB ram. I'm supposedly on a 7 mbps DSL line (but I have never gotten more than 5 mbps from Century Link) 
If anyone can talk me through a fix - I would appreciate it.
This is well beyond my capability.

---

### Post by QIII on 2016-09-26
Would you please run

```
top
```

and post back the first 8 or 10 lines of the bottom portion?

---

### Post by Gnusboy on 2016-09-27
Qll
Thankks for responding. Is this what you need?

```

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND     
 1116 root      20   0  329224  73604  55072 R  96.3  1.9 167:29.03 Xorg        
 6938 ranhanr+  20   0 1936664 869196 105460 R  82.0 22.9   8:00.54 firefox     
 6223 ranhanr+  20   0  762632  35424  22368 S  27.2  0.9   6:55.26 gnome-syst+ 
 1838 ranhanr+  20   0 1612152  84780  14600 S   9.6  2.2  35:31.39 compiz      
 7143 ranhanr+  20   0  724568  19604  12712 S   3.3  0.5   0:00.78 gnome-term+ 
   47 root      20   0       0      0      0 S   0.7  0.0   1:08.65 kworker/1:1 
   70 root      20   0       0      0      0 S   0.7  0.0   1:10.99 kworker/3:1 
  704 syslog    20   0  255836   2976    604 S   0.7  0.1   2:45.08 rsyslogd    
   10 root      20   0       0      0      0 S   0.3  0.0   0:16.23 rcuos/2     
   69 root      20   0       0      0      0 S   0.3  0.0   1:01.76 kworker/2:1 
  164 root      20   0       0      0      0 S   0.3  0.0   1:12.63 kworker/0:2 
 1692 ranhanr+  20   0   40408   2128    624 S   0.3  0.1   0:42.80 dbus-daemon 
 7192 ranhanr+  20   0   29140   1644   1128 R   0.3  0.0   0:00.09 top         
    1 root      20   0   33768   1984    748 S   0.0  0.1   0:01.31 init        
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.01 kthreadd    
    3 root      20   0       0      0      0 S   0.0  0.0   0:00.11 ksoftirqd/0 
    5 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/0:+
```

---

### Post by QIII on 2016-09-27
Hello!

OK. A few more questions:

What release of Ubuntu are you using?
What effects do you have enabled?
What graphics hardware do you have?
Are you using an open source or proprietary driver?
Do you have only a single tab open in firefox.
If you close Firefox, does Xorg drop to a more reasonable level?

---

### Post by Gnusboy on 2016-09-28
QIII
Thanks

I'm using Unbuntu 14.04
I'm not sure about the effects. Are you asking for which preferences/applications I have enabled? i.e. AdBlock,  
Graphics - Gallium 0.4 on AMD RS780 built in to Asus M3A78-EM
Driver: Open Source
Single tab open


Xorg seems to stay pretty even with Firefox open or closed.

 
Full String:
 

 [https://ubuntuforums.org/showthread.php?t=2338315](https://ubuntuforums.org/showthread.php?t=2338315)

---

