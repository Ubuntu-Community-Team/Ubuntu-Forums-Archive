---
title: "HDParm sometimes uses hdparm.conf, sometimes doesn't"
date: 2016-12-16
forum: Hardware
---

### Post by a.c.m on 2016-12-16
Hello community,

I got a system with a 120gb ssd m.2 for the OS and a raid1 2x2TB for media storage. The problem is with hdparm, it sometimes uses hdparm.conf to put the drives to sleep, it sometimes doesn't. If I manualy do hdparm -Y on both drives, then then stay in standby without problems, until a query comes up. Dunno where to start debugging. Can anyone suggest a starting point ?

this is the hdparm conf: [http://pastebin.com/eFJZmxQ4](http://pastebin.com/eFJZmxQ4)
this is the raid md0 info: [http://pastebin.com/WEYKh0FP](http://pastebin.com/WEYKh0FP)
this is the dmesg, lshw --class disk and hwinfo --disk output: [http://pastebin.com/4xLjyiB6](http://pastebin.com/4xLjyiB6)

hddtemp /dev/sda && hddtemp /dev/sdb
/dev/sda: WDC WD20EARS-00MVWB0: 42°C
/dev/sdb: WDC WD20EARS-00J99B0: 47°C
hddtemp /dev/sda && hddtemp /dev/sdb
/dev/sda: WDC WD20EARS-00MVWB0: 42°C
/dev/sdb: WDC WD20EARS-00J99B0: 47°C



I've checked the I/O for sda and sdb with dstat -D sda and dstat -D sdb to see if there are any querys, but they aren't. And it's logical too, since the drives don't wake up after I put them to sleep manually.

Any help is appreciated. Thank you.

---

### Post by a.c.m on 2016-12-19
Ok, so after 2 days of extensive, excruciating testing through trial and error, I've found out that the culprit was udisks. After I've purged it, the system works flawlessly.
It is a dual head HTPC with the main VT7 focus on Kodi, and a secondary VT10 for Xfce4 stuff. Now it doesn't matter if I acces xfce and leave apps open, or play and stop kodi content, immediatly as I stop. the HDDs are going quit and after 30mins they go to sleep. It is a beauty.

Thanks for the support.

12_19_2016_09:09:57
standby
standby
12_19_2016_09:19:57
standby
standby
12_19_2016_09:29:57
standby
standby
12_19_2016_09:39:57
active/idle
active/idle
12_19_2016_09:09:57
standby
standby
12_19_2016_09:19:57
standby
standby
12_19_2016_09:29:57
standby
standby
12_19_2016_09:39:57
active/idle
active/idle

---

