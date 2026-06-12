---
title: "Disk I/O taking exhorbitant CPU"
date: 2005-12-06
forum: General Help
---

### Post by elehack on 2005-12-06
I'm currently running Ubuntu Breezy on my laptop with a custom-built 2.6.12 kernel, using ReiserFS for both filesystems (root and home). Each FS is about 15G.

The disk I/O performance seems to be really bad. When hard disk operations that are of any magnitude at all are happening, the CPU is jacked to 100% consumed, taken up in the IOWait category. The entire system lags, feeling like it's running in molasses, whenever any process is doing anything substantial with the disk. I don't recall having these kinds of performance issues when I was running Gentoo or Debian (with similarly configured kernels).

The disk is running in DMA mode. I'm usually running with the CPU governed by powernowd, which keeps it at 600MHz most of the time; however, locking the speed up to 1.7GHz (the max) doesn't help much.

I'm listening to a CD right now using digital extraction, and it is causing no problems.

I've been suspicious of inotify, but that doesn't seem right, as I'm noticing the performance problems on reads as well as writes. I switched my root filesystem from XFS to ReiserFS in hopes of fixing it, and it may have improved it some, but not very much. I've contemplated switching to ext3, but I've had some severe data corruption problems with it in the past.

So, any ideas/advice as to why so much CPU is being consumed and what I can do to make the system more responsive would be appreciated. Reliability is important, so I'm reluctant to try strange hdparm tricks.

---

### Post by gcbzzzz on 2007-11-03
same here. when the notebook in question get's back to life i will post lspci

---

### Post by antares8 on 2007-11-16
the same problem with me. Using regular ubuntu gutsy kernel generic. Any ideas?

see thread: [http://ubuntuforums.org/showthread.php?t=545807](http://ubuntuforums.org/showthread.php?t=545807)

---

