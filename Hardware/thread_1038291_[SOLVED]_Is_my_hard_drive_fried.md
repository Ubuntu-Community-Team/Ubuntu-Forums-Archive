---
title: "[SOLVED] Is my hard drive fried?"
date: 2009-01-12
forum: Hardware
---

### Post by jmc1 on 2009-01-12
After shutting down my computer improperly (not too smart but the thing was frozen) I restarted it to find the system (running Ubuntu 8.10 desktop of course) lock up and display that the sda1 softreset failed, and after several failed attempts it pulled up some kind of shell (called ash or something). I booted from the CD, and though the system booted it didn't recognize the drive's existence apart from the softreset errors.

Is my hard drive fried then? I just finished up putting all my data on the hard drive to use the system as a backup home server - perhaps a really bad idea :( The hard drive is only 1-2 years old.

---

### Post by oilchangeguy on 2009-01-12
i don't think the drive is dead. probably a corrupt file. although it is strange you can see the hd via the live cd.

---

### Post by jmc1 on 2009-01-12
That sounds like good news - any idea how to fix the problem?

---

### Post by ajgreeny on 2009-01-12
start by running the live CD and typing ```
sudo fsck /dev/sdx#
```in terminal to do a file system check.  Make sure you know your device name for the ubuntu system install partition where I have put the sdx#.  That may be enough to get it up and running again.

---

### Post by jmc1 on 2009-01-12
Awesome, fixing it was just that easy. For the sake of learning more about Linux, what exactly did I just do? :D

---

### Post by ajgreeny on 2009-01-14
fsck is the filesystem check that ubuntu does by default every 30 boots, unless you change things manually.  what you did was run the same filesystem check from a live CD.  You can not run fsck on a mounted filesystem, so there is no way you can do it on ubuntu from the running installed system, hence the live CD way of running it with the filesystem unmounted.

It appears that the check did the trick and presumably put right any errors it found, so hopefully all will be OK now, (or at least until the next power failure or frozen system).  Incidentally, the journalled ext3 file system that ubuntu uses by default is far better at recovering after a power failure or forced reboot, than ntfs, and I think you were very unlucky to find yourself in this position.

---

