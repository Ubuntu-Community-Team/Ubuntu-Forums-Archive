---
title: "Samsung HD300LD partitioning problems through USB enclosure"
date: 2007-05-06
forum: Hardware &amp; Laptops
---

### Post by tams on 2007-05-06
I can't use the drive on my laptop because the partition table may be messed up and I've ran out of ideas on how to fix it.

I have a Samsung HD300LD hard drive sitting in a Prolific PL3507 USB enclosure. I know about the quality of the PL3507 chip, but the issue here is not related to the chipset.

I had an NTFS partition on the drive and was copying files happily on Kubuntu Dapper with NTFS-3G when a power outage came and the NTFS partition became inaccessible. Since I was unable to get it working on my laptop I installed it into the family desktop and magic! It worked.

I gave the HDD to a friend (using Ubuntu Feisty) who repartitioned it for me and it worked fine there. Now, at home the partition is unaccessible. It must be somehow related to the messed up partition table + enclosure situation therefore.

GParted wants to create a disklabel (on the disk that has actual filesystems) but fails.

What steps do I have to take to find out how to revive the disk?

---

### Post by tams on 2007-05-07
Checked syslog, this is what I get when starting GParted:

```
May  7 21:18:41 tams-laptop kernel: [ 5060.900000] printk: 813 messages suppressed.
May  7 21:18:41 tams-laptop kernel: [ 5060.900000] Buffer I/O error on device sdc, logical block 0
May  7 21:18:41 tams-laptop kernel: [ 5060.900000] Buffer I/O error on device sdc, logical block 1
May  7 21:18:41 tams-laptop kernel: [ 5060.900000] Buffer I/O error on device sdc, logical block 2
May  7 21:18:41 tams-laptop kernel: [ 5060.900000] Buffer I/O error on device sdc, logical block 3
May  7 21:18:41 tams-laptop kernel: [ 5060.900000] Buffer I/O error on device sdc, logical block 4
May  7 21:18:41 tams-laptop kernel: [ 5060.900000] Buffer I/O error on device sdc, logical block 5
May  7 21:18:41 tams-laptop kernel: [ 5060.900000] Buffer I/O error on device sdc, logical block 6
May  7 21:18:41 tams-laptop kernel: [ 5060.900000] Buffer I/O error on device sdc, logical block 7
May  7 21:18:41 tams-laptop kernel: [ 5060.908000] Buffer I/O error on device sdc, logical block 0
May  7 21:18:41 tams-laptop kernel: [ 5060.908000] Buffer I/O error on device sdc, logical block 1
```

---

### Post by tams on 2007-05-19
Turns out it was a hardware problem: one of the pins was pushed back.

---

