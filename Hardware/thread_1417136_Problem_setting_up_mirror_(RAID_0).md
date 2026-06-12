---
title: "Problem setting up mirror (RAID 0)"
date: 2010-02-26
forum: Hardware
---

### Post by shortmort37 on 2010-02-26
I wish to mirror my system drive to a secondary drive (configuration attached).  Here's what I get when I attempt to do so:

dan@ubuntu:~$ sudo mdadm --create --verbose /dev/md0 --level=0 --raid-devices=2 /dev/sda1 /dev/sdb1
[sudo] password for dan: 
mdadm: chunk size defaults to 64K
mdadm: Cannot open /dev/sda1: Device or resource busy
mdadm: /dev/sdb1 appears to contain an ext2fs file system
    size=488384000K  mtime=Wed Dec 31 19:00:00 1969
mdadm: create aborted

What are my next steps?

adTHANKSvance
Dan

---

### Post by paulisdead on 2010-02-27
Ya, you're wanting RAID1, not 0.  RAID1 is mirroring, RAID0 is striping.  Try this [http://ubuntuforums.org/showthread.php?t=1027240](http://ubuntuforums.org/showthread.php?t=1027240)

---

### Post by shortmort37 on 2010-02-27
OK, I want RAID1.  And, not to sound like I'm carping, or anything... But that 4 page recipe reads like stereo instructions.  Is there no easier way to mirror my hard drive, e.g., by building a bootable CD and raiding the two?

I thought Ubuntu was supposed to be the answer to Windows.  I buy in -- to a point.  But this approach is not for mere mortals.

Sorry.

Dan

---

### Post by paulisdead on 2010-02-27
Converting a working system's partitions to RAID is not a simple procedure.  Have you considered just backing up your data and reinstalling using the alternate install CD?

---

### Post by shortmort37 on 2010-02-27
What if the system isn't "working"?  i.e., if you're booted off of a CD -- is there no way to clone A to B, and RAID1 them at the same time?

---

