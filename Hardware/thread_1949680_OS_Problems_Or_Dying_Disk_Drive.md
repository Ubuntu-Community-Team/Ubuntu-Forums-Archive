---
title: "OS Problems Or Dying Disk Drive?"
date: 2012-03-30
forum: Hardware
---

### Post by playing_with_matches on 2012-03-30
Running Ubuntu 10.04 for a while now, and lately, my computer has been running a lot slower, crashes more often, and when I attempt to boot up, I often get a "Read Error" upon booting.

In order for me to start my machine, I need to shut it off a good 20-30 times before the "Read Error" disappears and I can get to the GRUB menu.  I am in the process of backing up all my important files, but does this sound like an OS issue or a hardware issue?

---

### Post by Yellow Pasque on 2012-03-30
It sounds like a hardware issue (hopefully, it's just the disk). If you run off of a livecd, do you have the slowness/crashing?

---

### Post by QIII on 2012-03-30
If all is well in a live session as suggested, can you do a SMART self test in your BIOS?

How about installing smartmontools in a live session and running the checks from there?

---

### Post by LinuxFan999 on 2012-03-31
You can also use the disk utility to run a SMART self test. It also shows the current SMART data.

---

### Post by playing_with_matches on 2012-03-31
Thank you, I am running Live Session now, it definitely has to be the disk, as now when I boot it doesn't even recognize the partition (Partition doesn't exist error).

I will attempt to run a SMART test on it, is it possible to do from the live disk?  Also, I must say, the Live Disk is a god send as far as backing up files go.

---

### Post by LinuxFan999 on 2012-04-01
> **playing_with_matches said:**
> Thank you, I am running Live Session now, it definitely has to be the disk, as now when I boot it doesn't even recognize the partition (Partition doesn't exist error).
 
I will attempt to run a SMART test on it, **is it possible to do from the live disk?** Also, I must say, the Live Disk is a god send as far as backing up files go.
Yes, it is possible.

---

### Post by ahallubuntu on 2012-04-01
I usually use a Parted Magic CD (also included on the Ultimate Boot CD) to test S.M.A.R.T. on a computer where the drive isn't bootable or is suspect.  Parted Magic is a super handle utility disk to have around - it's a Linux distro with all kinds of handy little tools in it.  You can certainly do SmartMonTools from a live CD, but Parted Magic makes it much easier.

---

### Post by Mark Phelps on 2012-04-04
I believe that fsck (file system checker) will run automatically every 30 boots.  So, if you have to shut it off and reboot that many times, it could be that fsck is running and repairing (temporarily) the file system problems -- allowing you to then boot correctly.

But, if the drive is failing, when you reboot later, you're going to encounter new filesystem corruption -- and have to go through this again.

---

