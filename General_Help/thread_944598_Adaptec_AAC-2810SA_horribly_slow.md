---
title: "Adaptec AAC-2810SA horribly slow"
date: 2008-10-11
forum: General Help
---

### Post by Cr0n_J0b on 2008-10-11
I'm wondering if anyone has experience with the adaptec raid controllers.  I just setup a new build with an AAC-2810SA.  with Hardware RAID5 and a 4 drive RAID set I'm getting like 4-7MB/sec.  my single boot drive is doing loads better than that.  I'm just wondering what I might be missing here.  I've tested performance with Bonnie++ and IOZONE3 as well as just timed writes.  all show the adaptec being extremely slow.

thanks

---

### Post by fjgaude on 2008-10-11
Is your memory and CPU modern, fast?

---

### Post by Cr0n_J0b on 2008-10-12
Well, it's all relative I guess.  The system is running a P4 2.0GHz processor with DDR2 memory, but I wouldn't say it's a screamer.  The issue is that with the single IDE drive I can get 20-30MB/s but with hardware RAID I can only get aroung 10MB/s...which doesn't seem right.  I'm guessing that either I need to setup some drive differently or there some strangeness going on.

---

### Post by fjgaude on 2008-10-12
Well, with raid5 you need some CPU power to handle the parity writes on each drive... if you wish to experiment, try raid0 with three or four drives, no parity writes. That should show if software/hardware raid with your setup works to increase thruput from the drives.

Question: does the controller work off a PCI bus?

---

### Post by Cr0n_J0b on 2008-10-12
Well, I've done a bunch of experiments.  I'm using dbench as the test application, since it's pretty fast and easy for the first pass.  I'm using 110 clients and 90 second runs.

on my base linux system: P4 2.0GHz, 2GB RAM DDR2 800, AAC-2810SA PCI-X hardware RAID controller, 4 x SATA onboard.  Disks are Hitachi 500GB SATAII drives (7200rpm).  Ubuntu 8.04 and the adaptec driver loaded (not sure if it's working).

/dev/sdf -- single drive -- ATA -- 51.45MB/s
/dev/sda -- Hardware RAID5 -- SATA -- 11.49MB/s
/dev/md3 -- Software RAID5 -- SATA -- 7.39MB/s
/dev/md0 -- Degraded SW RAID 5 -- SATA -- 2.92MB/s
/dev/dsb1 -- single drive off HW controller -- SATA -- 25MB/s
/dev/md3* -- Software RAID0 -- SATA -- 41.64MB/s
/dev/sdb1 -- Hardware RAID0 -- SATA -- 23.28MB/s
On a second system I have tested some other software variants

System 2 Opteron 180 2GHz, 2GB DDR, SATA II same drives and OS

/dev/sda -- single drive -- ATA -- 45.66MB/s
/dev/md0 -- SW RAID5 -- SATA II -- 19.045MB/s

The difference between the SATA and SATA two is because the HW Raid controller only supports SATA I, while the motherboard has SATAII ports.

I'm expecting to get a different RAID card next week, so I'll test that out as well.  As of right now, I'm leaning toward SW RAID0 as that's the only way to get it to give me the numbers I need.

---

### Post by fjgaude on 2008-10-12
I don't have any experience with **dbench**, except just run it with 100 clients, 600 seconds, using the default client.txt file. With that I get in the range of 800MB/sec readings, execute.

I don't know how to check drive by drive. How did you get it to do that?

---

### Post by Cr0n_J0b on 2008-10-12
dbench, bonnie and iozone all run against the filesystem you are currently positioned in...so I just switched from one fs to another.

---

### Post by fjgaude on 2008-10-13
> **Cr0n_J0b said:**
> dbench, bonnie and iozone all run against the filesystem you are currently positioned in...so I just switched from one fs to another.

Okay, I switched to running **dbench** from my raid5 and got about 425MB/sec... from my boot drive I got in the 800MB/sec range. I used the default settings as I said before.

I get about 100MB/sec using **hdparm** on the boot drive, and about 200 on the array.

Understand I have a very fast workstation... notice my signature. <smile>

---

### Post by Mustang Matt on 2009-07-23
Cr0n, Did you ever figure this out? I'm having the similar results.

bonnie++ gave me reasonable enough numbers but transferring between two arrays on the same adaptec card was terribly slow. 3-9 M/s but averaging on the lower side.

Any thoughts on how I can trouble shoot this?

---

