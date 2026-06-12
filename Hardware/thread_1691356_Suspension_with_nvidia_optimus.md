---
title: "Suspension with nvidia optimus"
date: 2011-02-19
forum: Hardware
---

### Post by dmar0 on 2011-02-19
Hey everyone!

I can't get to work the suspension for my Dell XPS 15 (L501X) laptop. When I hit suspend, I get right away to the login window, as if I would press lock screen and not suspend. 

I know that suspension usually depends on the video chip, and here might be the problem. I have 2 video cards on the laptop:

```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller ( rev 18 )
02:00.0 VGA compatible controller: nVidia Corporation Device 0df1 (rev a1)
```

However, same as everyone else with two video cads, I can use only Intel under Linux. The desktop effects are working fine, nevertheless I have NO nvidia drivers. 

I searched much regarding this issue, however I could not find anything that would help.

I also tried the the uswsusp utility ([http://ubuntuforums.org/showthread.php?t=471855](http://ubuntuforums.org/showthread.php?t=471855)) with various options, but nothing seems to help.

Any ideas regarding how to make suspension work will be much appreciated!

Thank you! ;)

---

### Post by Slave2Metal on 2011-02-19
[B] 	This is the title of the thread you need.

[SOLVED] Dell XPS 15 (L501X) Suspend Mode Fix on Ubuntu 10.10  [/B]

---

### Post by dmar0 on 2011-02-20
Thank you much for the suggestion! Found the topic, applied the fix and it worked!

Thanks! :)

---

### Post by Hotwheelz79 on 2011-02-21
Hi dmar0,

Do you have the following config?

Dell XPS 15
Intel(R) Core(TM) i5-480M processor(2.66GHz, 
15.6 FHD (1920x1080) B+RGLED display with TrueLife™
8GB Dual-channel 1333MHz DDR3 SDRAM 
750GB 7200RPM Hard Drive
Tray Load Fixed Blu-ray BD-ROM / DVD + /-RW Combo Drive
1GB NVIDIA® GeForce® GT 420M graphics (with WIDI)

Thanks.

8)

---

