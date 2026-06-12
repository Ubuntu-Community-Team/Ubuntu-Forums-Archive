---
title: "What happens if a drive in RAID 1 fails?"
date: 2008-07-29
forum: General Help
---

### Post by MikeBenza on 2008-07-29
I have a RAID 1 (mirrored) array set up with mdadm.  Suppose a drive in the array fails.  If I replace the drive and create a partition the same size as was part of the RAID, will the machine automatically update the new drive to be a mirror?  How does it know which is the new drive and which is the drive with important files on it?

- Mike

---

### Post by kool_kat_os on 2008-07-29
magic? :)

sorry for not being useful...but i had to say that

---

### Post by fjgaude on 2008-07-30
It  knows, mdadm, by the way you have to prepare the drive to be added to the array. The **UUID** created is the same for each drive and for the array.

Might be helpful to read, study:

[http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)
   then study **/usr/share/doc/mdadm/FAQ.gz** and **md.txt.gz**

Good luck!

---

### Post by finite9 on 2008-07-30
isnt there a command to add a device to the array?  this wont happen automatically just because you add a new drive.  read the mdadm man page, it has examples.

---

