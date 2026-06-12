---
title: "windows often freezes after Ubuntu installed on Dell laptops"
date: 2009-09-07
forum: Hardware
---

### Post by hcen on 2009-09-07
Dear Ubuntu Experts ,

Months ago I installed Ubuntu 8.04 as a dual boost to my Dell Studio laptop (Windows Vista, Intel Core 2 Duo, 140G HD, 3Gb Mem, 17'' screen). After the installation, my windows operation system often freezes for no reasons. I notice that most of the time, the freezes occur after the system sits idle for a while (like 10 minutes) and then suddenly I want to open/write a document. The freezes occur less frequently when I keep machine busy. 

The same problem happened to my another 3-year olde Dell laptop with WinXP, Intel Core Duo after I added Ubuntu as a second operating system. 

Please advice how to deal with this issue.

thanks a lot

Hao

---

### Post by lykwydchykyn on 2009-09-07
Well, simple; uninstall Windows, problem solved!  :-) 

j/k

Seriously, I'm having a hard time imagining a scenario where the mere presence of Ubuntu somewhere else on the hard drive would cause Windows to freeze up.

Is this a Wubi install or a true dual-boot scenario (i.e., did you install ubuntu by running the installer from within Windows, or by booting to the disc?)

Did you leave enough room for Windows to work?  How much free space is on the Windows partition?

Are there any error messages in the Windows Event Log?

Have you tried updating video/audio/network/BIOS drivers for Windows?

---

### Post by RabidWeezle on 2009-09-08
The only thing I can think of is you shrunk your windows partition too much and it can't make it's memory swapfile. Then the best thing you can do is free up some hard drive space on the windows partition so it can get it's swapfile in there. Windows doesn't run well on a full partition.

---

### Post by hcen on 2009-09-08
Hi [lykwydchykyn]("http://ubuntuforums.org/member.php?u=603141") and [RabidWeezle]("http://ubuntuforums.org/member.php?u=314464"),

thanks for your quick reply. 

This is a clarification on what I posted. I installed Ubuntu as  a true dual-boot , not by Wubi. My Windows C partition has 40GB free of 122GB and a recovery partition with 4.5Gb free of 10 Gb. 

Is the free space enough for a Windows partition?

What events shall I look at in Event Viewer?

When I am using ubuntu, I noticed occasional freezing in ubuntu too. 

best

Hao

---

### Post by lykwydchykyn on 2009-09-08
> **hcen said:**
> 
Is the free space enough for a Windows partition?

That ought to be sufficient
> 
What events shall I look at in Event Viewer?

Anything with a big red X next to it (or whatever icon Vista is using for errors these days).  Though I wouldn't count on them being too helpful.

> 
When I am using ubuntu, I noticed occasional freezing in ubuntu too. 

If it's freezing in both, that may very well point to a hardware issue.  At the very least, it's worth running memtest and checking the hard drive for physical errors (try "badblocks" on the Linux command line).  Dells usually have some kind of hardware diagnostics built in, which you can select if you hit "f12" during boot.

---

### Post by hcen on 2009-09-09
Hi [lykwydchykyn]("http://ubuntuforums.org/member.php?u=603141"),

Thanks. I tried the memtest and badblocks and didn't see any problems. 

Another scenario where freezing are likely to occur is when I launch Windows Explorer or open as Save As dialog. Do you think it could be caused by page miss due to the ubuntu partition on the hard drive?

best

Hao

---

### Post by lykwydchykyn on 2009-09-09
> **hcen said:**
> Hi [lykwydchykyn]("http://ubuntuforums.org/member.php?u=603141"),

Thanks. I tried the memtest and badblocks and didn't see any problems. 

Another scenario where freezing are likely to occur is when I launch Windows Explorer or open as Save As dialog. Do you think it could be caused by page miss due to the ubuntu partition on the hard drive?

best

Hao

I couldn't say for sure.  Though in theory it *shouldn't* be a problem.  Maybe try running chkdsk /r from your Windows CD (if you have one).  Unfortunately chkdsk never tells you what problems it has fixed (though I've yet to see it run without finding any), but it's about the only way I know of to sort out filesystem-level issues on Windows.

---

