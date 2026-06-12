---
title: "Slow USB speeds not limited to USB."
date: 2008-09-29
forum: General Help
---

### Post by detroit/zero on 2008-09-29
[I've been]("http://ubuntuforums.org/showthread.php?t=911052") [ranting about]("http://ubuntuforums.org/showthread.php?t=793688") [slow USB]("http://ubuntuforums.org/showthread.php?t=895386") [transfer speeds]("http://ubuntuforums.org/showthread.php?t=909158") for, like, two months now.

Much to my surprise, the ridiculously slow USB file transfer speeds are not limited to transfers to USB devices.

After selecting a bunch of videos in my Videos folder, I accidentally hit the delete key and moved everything to the trash folder. I went into the trash folder, hit ctrl-a to select all, and ctrl-x to cut all the files. 

Trying to paste them back to /home/zero/Videos gives the same super-slow transfer speed (less than 5MB/s to start and getting slower by the second), makes my GUI sluggish and unresponsive, and is taking over 30 minutes to move 6.5GB of media files from trash to videos.

My home dir resides on its own partition, and I realize that reading from and writing to the same physical HDD us going to cause somewhat of a slowdown, but my transfer speed right now is 4MB and dropping.

[This post]("http://ubuntuforums.org/showpost.php?p=5758666&postcount=9") highlights some of what I found concerning the USB problem, but now that I know for a fact that it's not limited to USB transfers, I don't know what to think.

---

### Post by AyAn4m1 on 2008-10-08
I'm not sure if you've tried this already, but adding "irqpoll" to the kernel line of my bootloader entry resolved similar issues that I was having on Hardy x64. I can't boot without "pci=routeirq" as well, so for all I know you need both to fix the issue, but adding irqpoll allowed me to watch video off of my USB drive for the first time in Hardy.

---

### Post by detroit/zero on 2008-10-09
> **AyAn4m1 said:**
> but adding irqpoll allowed me to watch video off of my USB drive for the first time in Hardy.
That's interesting, and I think I'll give it a shot next time I reboot.

Thing is, for me, read speeds have never been an issue. I still get read speeds from USB devices in the 25-30MB/s range; write cycles are where the slow downs occur.

---

### Post by detroit/zero on 2008-10-19
Since the slow USB write problems aren't limited to Ubuntu, and seem to apply to various distros and kernel versions over the last few years, I started [a thread over at Linuxquestions.org]("http://www.linuxquestions.org/questions/linux-hardware-18/slow-usb-write-speeds.-677588/")
 
 Maybe the people who are having this problem can all get together and find a fix, rather than wait to see what trickles down from on high.
 
 Come over there and chime in with your experiences with the slow USB write speeds.

---

