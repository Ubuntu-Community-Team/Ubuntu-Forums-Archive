---
title: "Need help rebuilding RAID 1 array"
date: 2007-10-17
forum: Hardware &amp; Laptops
---

### Post by matty_x on 2007-10-17
I've got an issue that appears to be confounded by multiple factors. In essence, what I am attempting to accomplish is to rebuild a RAID 1 mirrored array.

**History:**

The system was installed as a storage server with three drives. One drive held the operating system. The other two were mirrored using RAID 1.

The drive that held the operating system failed last week. The data cannot be recovered. It is beyond help.

The RAID drives are fine.

**The problem:**

I set up the RAID array over a year ago. It was the first time I set up a RAID array. I no longer recall the specifics of the setup process. I now want to rebuild the array and transfer the data to an external hard drive so that I can install the operating system on one of the remaining drives.

I would like to use the Ubuntu live CD to get an operable system, then download mdadm via apt-get, and use that to rebuild the RAID array. However, I cannot seem to get the system to recognize the RAID drives at all. Poring through the information in the device manager did not offer me any clues--the only "/dev/" entry I could  find was for the CD/DVD writer. Could this be due to the fact that they configured as RAID drives? What shell commands might give me a listing of the drives that are on my system (but not necessarily mounted)?

The way I see it, I need to first get the system to recognize the drives. After this, I can tell mdadm to rebuild the drives. And after this I can transfer the data to an external drive.

Many thanks!

---

### Post by matty_x on 2007-10-18
bump

---

### Post by psusi on 2007-10-18
Have you unplugged the failed drive?

---

### Post by h0me5k1n on 2007-10-21
I'm interested to hear how this would be done......

I have a similar configuration.  I have 3 drives set up in the same way as you - the first drive is mounted to "/" and the two other drives are a RAID1 set mounted to "/home".  I actually have my data backed up elsewhere too until I figure out how I will recover the data if the "/" disk fails!!

Does "fdisk -l" show the drives/partitions from the RAID set?
Which version of the live CD are you using?

Everything I'm reading about RAID seems to say that when you create the array the disks will be formatted but in our case we don't want to create a new array - we want to recover the old one!

---

