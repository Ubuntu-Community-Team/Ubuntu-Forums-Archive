---
title: "Constan High CPU usage"
date: 2009-08-08
forum: Hardware
---

### Post by keithclark on 2009-08-08
My CPU always seems to be at 100%.  Even upon first bootup.  It shoots straight for 100% and stays there for days.

Here is my top report:

top - 00:00:28 up 1 day, 10:11,  6 users,  load average: 6.45, 6.22, 5.73
Tasks: 220 total,   8 running, 212 sleeping,   0 stopped,   0 zombie
Cpu(s): 73.8%us, 25.2%sy,  1.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2989272k total,  2969800k used,    19472k free,    82800k buffers
Swap: 11687248k total,    40232k used, 11647016k free,  1434232k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
31273 keithcla  20   0  168m  20m 5108 R 22.2  0.7  17:18.89 mencoder           
21957 root      20   0  493m 200m  22m S 12.9  6.9  65:37.07 Xorg               
22052 keithcla  20   0 30616 9.9m  660 S  7.0  0.3  22:13.13 dbus-daemon        
21993 keithcla  20   0  169m 8284 6156 R  2.7  0.3  14:41.42 x-session-manag    
22060 keithcla  20   0 47644 7424 2364 S  2.3  0.2  10:27.53 gconfd-2           
29572 keithcla  20   0  223m  36m  13m R  2.3  1.2   1:19.99 python             
22095 keithcla  20   0  245m  34m 8980 S  2.0  1.2   9:35.45 compiz.real        
23881 keithcla  20   0 1321m 115m  45m S  2.0  4.0   7:39.75 amarok             
16519 keithcla  20   0  219m  17m 8124 S  1.7  0.6   2:08.65 awn-applet-acti    
 5654 keithcla  20   0     0    0    0 R  1.3  0.0   0:00.04 vino-server        
22217 keithcla  20   0  237m  27m 9332 S  1.0  0.9   4:37.05 indicator-apple    
22473 keithcla  20   0  158m 6004 4132 S  1.0  0.2   4:16.13 gnome-screensav    
  754 keithcla  39  19 58612  33m 3052 R  0.7  1.1   0:02.89 apt-check          
 5823 chipcard  20   0 27588 1396  860 S  0.7  0.0  11:53.37 chipcardd4         
22089 keithcla  20   0  228m  17m 8220 S  0.7  0.6   5:06.84 gnome-settings-    
 2611 keithcla  20   0  347m  41m  16m S  0.3  1.4   0:01.68 python             
 2722 boinc     20   0 67032 4828 2580 S  0.3  0.2   2:58.68 boinc              
 4774 keithcla  20   0 19116 1412  988 R  0.3  0.0   0:00.22 top                
 5655 keithcla  20   0  208m 6620 5080 R  0.3  0.2   0:00.01 vino-server        
 6884 keithcla  20   0  681m  76m  24m S  0.3  2.6   2:58.92 evolution          
10901 keithcla  20   0  710m 262m  29m S  0.3  9.0  12:27.29 firefox            
16510 keithcla  20   0  212m  16m 9524 S  0.3  0.6   1:08.13 awn                
22057 keithcla  20   0  299m 6400 4600 S  0.3  0.2   8:46.72 pulseaudio         
22096 keithcla  20   0  357m  32m  18m S  0.3  1.1   3:21.29 gnome-panel        
22097 keithcla  20   0  498m  55m  20m S  0.3  1.9   2:59.42 nautilus           
22105 keithcla  20   0  139m  12m 5360 S  0.3  0.4   1:14.51 trackerd           
22113 keithcla  20   0  248m  25m  11m S  0.3  0.9   3:46.22 python             
22118 keithcla  20   0  173m  15m 8868 S  0.3  0.5   0:53.55 notify-osd         
22139 keithcla  20   0  292m  34m  13m S  0.3  1.2   1:57.65 ubuntuone-clien    
22141 keithcla  20   0  224m  10m 6508 S  0.3  0.4   1:22.17 gnome-power-man    
22262 keithcla  20   0  136m  29m 5064 S  0.3  1.0   0:52.57 ubuntuone-syncd   

Yes, I am running mencoder now, but when I shut that off (complete the job) the cpu still stays at 100%.

Not sure how to trouble shoot further.  I think this might be related to all the 

Aug  7 23:10:38 HP1211N kernel: [120099.281502] serial8250: too much work for irq17

lines I see in my logs.  There are tons of them.

Keith

---

### Post by mikewhatever on 2009-08-08
Why don't you post the output of ps aux without mencoder, or even better, ps aux > Desktop/process.txt, and attach process.txt file from your desktop to the next post.

---

### Post by SecretCode on 2009-08-08
No expert here, but it looks like Xorg is chewing up CPU. To check which are the busiest processes since you booted, post the results of

```
ps -eo time,etime,pcpu,pid,comm|sort -r|head -20
```

If Xorg is the culprit - do you have compiz or other effects enabled? Do you have the right driver for your graphics card?

Be aware that high utilisation of Xorg can mean there's a problem in another process that calls Xorg, not necessarily in Xorg itself: [https://wiki.ubuntu.com/X/Troubleshooting/HighCPU](https://wiki.ubuntu.com/X/Troubleshooting/HighCPU)

---

### Post by keithclark on 2009-08-08
keithclark@HP1211N:~$ ps -eo time,etime,pcpu,pid,comm|sort -r|head -20
    TIME     ELAPSED %CPU   PID COMMAND
02:16:40    17:56:39 12.6 21957 Xorg
00:56:29    17:56:30  5.2 22052 dbus-daemon
00:33:59    17:56:31  3.1 21993 x-session-manag
00:25:05    17:56:30  2.3 22060 gconfd-2
00:21:43    17:30:54  2.0 10901 firefox
00:16:10    17:56:30  1.5 22057 pulseaudio
00:14:51  1-19:59:15  0.5  5823 chipcardd4
00:14:21    17:54:09  1.3 23881 amarok
00:11:38    17:56:27  1.0 22089 gnome-settings-
00:11:16    17:56:18  1.0 22217 indicator-apple
00:09:28    08:52:39  1.7  2057 compiz.real
00:08:51    17:56:25  0.8 22113 python
00:08:43    17:55:56  0.8 22473 gnome-screensav
00:08:24    08:08:42  1.7 24120 transmission
00:07:07    17:56:27  0.6 22096 gnome-panel
00:06:10    17:35:55  0.5  6884 evolution
00:05:48    17:56:26  0.5 22097 nautilus
00:05:16    17:49:18  0.4 27531 pidgin
00:04:31    17:54:04  0.4 23956 kded4

---

### Post by SecretCode on 2009-08-08
Xorg is the busiest then - definitely look at [https://wiki.ubuntu.com/X/Troubleshooting/HighCPU](https://wiki.ubuntu.com/X/Troubleshooting/HighCPU)

---

### Post by keithclark on 2009-08-08
Yeah, I've tried everything.  Turned everything off.  Still high cpu usage.

I'm using the open source drivers for my ATI X200 video card.  I use the very same chipset on my laptop and there is no issues there.  Same driver, same Ubuntu release.

Not sure what to do next.  This was a fresh install as well.  Maybe another completely different distro?

Keith

---

### Post by Yellow Pasque on 2009-08-08
I notice you're running tracker. If you end the tracker process(es), does that help the CPU usage?

For the serial8250 issue:
Are you running virtualbox? [http://www.virtualbox.org/ticket/2752](http://www.virtualbox.org/ticket/2752)

I would look for some way to disable the serial port if you're not using it. If you're running virtualbox, I would hope there would be some way to turn it off. If you're not running VB, you can probably blacklist the serial8250 module or turn it off in the BIOS if possible.

---

