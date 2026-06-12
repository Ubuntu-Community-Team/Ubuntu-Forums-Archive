---
title: "External hard drive problem"
date: 2007-06-09
forum: Hardware &amp; Laptops
---

### Post by joewatt on 2007-06-09
OK, so here's my problem. I am running Vista Ultimate installed on c: drive, internal. I wanted to install Ubuntu on an 80G or so partition of my 160G USB external hard drive, NTFS format, with another small partition as a place for a swap file.

The installation seemed to go fine, including reformatting the 80G partition, and the dual boot operation seemed to work well. Here's what went wrong. Now, Ubuntu runs well, but Vista can't see the external drive at all and Paragon Partition Manager (in Vista) shows all 3 partitions on the external drive as being formatted for Linux. THAT'S NOT WHAT I DID!!  And it certainly isn't what I wanted, because there's important stuff on those other partitions.

The thing is, when I first did the installation those other partitions were fine. This didn't happen during the installation, it happened later somehow.

Please tell me I can get those partitions back!

Joe

---

### Post by logos34 on 2007-06-09
If you had to shrink the ntfs windows paritions to make room for the 80gb linux, then you might want to run CHKDSK with repair option on them (from the vista install cd) to see if that sorts things and then you can access them in windows.  If you just formatted 80gigs worth of unallocated space, then it shouldn't have caused any problems. 

edit: 
> This didn't happen during the installation, it happened later somehow.

still, chkdsk might fix it.

Does linux see them ok?  How many paritions on the disk and what are they? You could run
sudo fdisk -l 
(i.e. the letter l) 

and post it.

---

