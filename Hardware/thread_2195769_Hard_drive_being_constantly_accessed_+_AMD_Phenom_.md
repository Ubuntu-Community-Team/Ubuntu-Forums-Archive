---
title: "Hard drive being constantly accessed + AMD Phenom running 100%"
date: 2013-12-26
forum: Hardware
---

### Post by evil elvis on 2013-12-26
I have a system I built myself a couple of years ago.  It has an AMD Phenom Quad core, 4GB memory (XMS2), 1 LG DVD/CD RW, 4 hard drives,1 ATA and 3 SATA,  I dual boot Ubuntu 12.04 and XP but spend 95% of my time in Ubuntu.

The problem:  I installed Lyx yesterday.  About an hour after doing so I noticed the system slowing down a great deal.  My HD's a rather quiet so I had to look at the access light for activity.  It was flickering rapidly and did not stop.  I was able to pull up System Monitor (have 2, not sure which) to try and discover some whacked out process.  Instead I discovered that even the drives (drive?) was in constant use, very little data was being moved around.  I also discovered that all 4 of the AMD's quad cpu's were being maxed out at 100%.  I had never seen this.  This little bit of investigation took almost three hours because of the usage.  It would normally have taken a couple of minutes.

I rebuilt the boot sector on the boot drive using Grub2.  No help.  I suspected it might be that drive as it is the oldest, WD Barracuda 7200.7) and the smallest (40GB).  It is also the XP drive.  Disconnected it, made no difference.  Put the 12.04 CD in the drive and the access stopped.  For about 10 minutes.  It then started right back up.

I am accessing this forum using a GhostBSD LiveCD.  The drives are currently quiet.  I have not found a utility under Ghost to look at the cpu's but since the system is acting normal, I suspect they are not being hammered.

Oh yea, the Smart feature is turned on in the BIOS for all of the drives and they are all reporting healthy.

I am puzzled.  Not sure if it is something in Linux or maybe I need to contact ASUS.  Idea's?

---

