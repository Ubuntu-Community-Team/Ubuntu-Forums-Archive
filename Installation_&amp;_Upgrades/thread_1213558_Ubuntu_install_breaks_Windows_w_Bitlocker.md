---
title: "Ubuntu install breaks Windows w/ Bitlocker"
date: 2009-07-14
forum: Installation &amp; Upgrades
---

### Post by 50words on 2009-07-14
I have a Thinkpad T400 running Vista Ultimate, with BitLocker enabled. I finally got around to installing Ubuntu (which I have run on several other computers for years). I used the Windows disk manager to resize the BitLocker partition, then installed Ubuntu on the freed space using LVM so I could set up separate / /home and swap partitions.

For some reason, the installer forced me to use LILO, which I am not familiar with, but I figured out how to get to the boot menu, so it will work just fine.

But when I rebooted and started up Windows, it wanted my BitLocker key. No biggie, I entered it, but Windows would not start. I tried launching the setup repair option, but again, no luck.

Any idea how to get my Windows partition working again?

---

### Post by Ubtuntu on 2009-07-15
While this doesn't solve your problem, it provides some general information about bitlocker requirement that might help you troubleshoot. 

[http://support.microsoft.com/kb/933246](http://support.microsoft.com/kb/933246)

It talks about Bitlocker needing two partitions on the drive. Did you hose one of these when you installed Ubuntu? Also talks about windows partition needing 10% free space, is it less than that after resize? You can probably identify other potential issues if you read it closer than I did and find a KB article more about post install issues than the linked one. It also talks about using some maintenance tool to repair a bitlocker install, maybe you can find that tool and try it. Good luck.

---

### Post by 50words on 2009-07-15
Thanks for the link. I actually read that over before trying to install Ubuntu, and there does not seem to be much helpful information there.

I am thinking it may be a problem with the MBR, but I cannot figure out how to fix that.

---

### Post by 50words on 2009-07-15
I guess I am going to have to figure out a way to create system recovery disks on another computer. Argh.

---

### Post by Mark Phelps on 2009-07-15
How many times did you run Startup Repair? If only once, don't despair.  Run it 2 or 3 more times.  It has been know to take several attempts to really repair Vista.

---

### Post by 50words on 2009-07-15
> **Mark Phelps said:**
> How many times did you run Startup Repair? If only once, don't despair.  Run it 2 or 3 more times.  It has been know to take several attempts to really repair Vista.

I tried a few times, but no go. Ordered the recovery disks today, since I did not make them beforehand.

---

