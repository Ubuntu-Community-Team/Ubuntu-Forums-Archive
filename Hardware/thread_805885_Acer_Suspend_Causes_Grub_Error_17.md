---
title: "Acer: Suspend Causes Grub Error 17"
date: 2008-05-24
forum: Hardware
---

### Post by alex941021 on 2008-05-24
Clean install of Ubuntu 8.04 Hardy on an acer Ferrari 5000 laptop.

Suspending to ram successfully suspends/standby the machine, however upon resume, it hangs, and nothing happens.  Removing proprietary drivers doesn't help either.  The only thing that will successfully shut down the machine is a hard power down.  

However, upon reboot, I get a GRUB ERROR 17 and at that point the file system is completely corrupted, and everything has to be reinstalled.  Tried this with a single root partition "/" or with a separate partition for "/boot" but still nothing good happens.

Any help would immensely appreciated.

Thanks!

---

### Post by exactt on 2008-06-04
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/203537](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/203537)

---

### Post by alex941021 on 2008-06-05
I've checked the thread, but none of the approaches seem to work.

> **exactt said:**
> [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/203537](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/203537)

---

### Post by exactt on 2008-06-06
i know. there is no solution. just wanted to let you know that the problem is known and you are not the only one suffering from it.

although running fsck left my file system as a pile of numbered directories i was able to recover almost all of my files.

hope your are lucky too and/or have your backups at hand.

cheers

---

### Post by alex941021 on 2008-06-06
Ok, thanks.  

What type of partitioning do you have?  I have a single large partition for all mount points.  Do you think having a separate partition for /boot will prevent the corruption for occurring. I am still not sure as to when the corruption occurs, 1) when the system is suspended (it seems that everything goes smoothly), or 2) when it tries to awake.The power management of the system seems to be running ok, as the suspend/resume feature works fine under vista or XP.  

Also, would any proprietary driver, or package cause this problem, or is this just a defect of the kernel and(or) power management system?

> **exactt said:**
> i know. there is no solution. just wanted to let you know that the problem is known and you are not the only one suffering from it.

although running fsck left my file system as a pile of numbered directories i was able to recover almost all of my files.

hope your are lucky too and/or have your backups at hand.

cheers

---

### Post by exactt on 2008-06-06
sorry i can't help you any further. just monitor/subscribe to the bug and wait what happens.

for what it's worth: i had 2 separated partitions / and /home . this didn't help much. both were smashed.
me and others have an nvidia graphics board and are using AMD64 version with nvidia-glx-new. if you don't have an nvidia graphics card maybe point that out in the bug report.

---

### Post by alex941021 on 2008-06-06
No problem.  What I was thinking is that placing /boot in a separate partition could prevent the corruption from occurring, and  as a result the boot (after a failure in standby/resume) could still occur.  However, I am not sure what is being corrupted and where the corruption is taking place.  I am 100% sure that during suspend/hibernate something is done to the filesystem, or disk that causes the error.  You know why, because if you were to hard powerdown your computer even while it is writing something to disk you might lose files, but not the all thing.  If you power it down while it is idle, you lose nothing.  For that reason I think that when we activate suspend, or when we are trying to resume something fires up that corrupts the all thing.  

BTW, I have an ATI video card, but that doesn't make any difference.  I also tried to remove all drivers, and the problem is still there.

---

