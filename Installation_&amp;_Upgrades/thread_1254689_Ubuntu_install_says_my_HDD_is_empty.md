---
title: "Ubuntu install says my HDD is empty"
date: 2009-08-31
forum: Installation &amp; Upgrades
---

### Post by vfontanela on 2009-08-31
[SOLVED]

Hello everyone,

I'm trying to reinstall my Ubuntu from zero, but when I get into the partitioning screen it says my Hard disk is empty, without any partition. But it has partitions.

I've already tried to mount the partitions - yes, the system mounts them, - and then run the install, but no success. I tried also to run:

sudo cfdisk

And all partitions are there.

[I]  Disk Drive: /dev/sda
                       Size: 160041885696 bytes, 160.0 GB
             Heads: 255   Sectors per Track: 63   Cylinders: 19457

    Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 
    sda1        Boot        Primary   NTFS             []             137181.22
    sda5        Boot, NC    Logical   Linux ext3                       21854.57
                            Logical   Free Space                           0.04*
    sda3                    Primary   Linux swap / Solaris              1003.46[/I]

Here there is a screenshot:
[http://yfrog.com/e8screenshotmksp](http://yfrog.com/e8screenshotmksp)


Thanks a lot for helping.

---

### Post by ugm6hr on 2009-08-31
If you are planning to reinstall, it doesn't matter.

You can just wipe everything and start again.

---

### Post by vfontanela on 2009-08-31
I can't because my back up is in other partition, as well as the other operational system I unfortunatelly still need to do some things.

I need it to show all the partitions so I can delete only the linux partitions and then create it again or make the partitioning part with cfdisk in a way Ubuntu install can recognizes it.

---

### Post by ugm6hr on 2009-08-31
Try the manual install option.

---

### Post by vfontanela on 2009-08-31
I tried, but it doesn't show my partitions.

I also tried to verify my partition table using fdisk, but no result.

---

### Post by tal007 on 2009-08-31
I absolutely agree with you. Proceed with some cautions. I can see NTFS boot  sector on your 1st partition. I also see Ubuntu boot loader on partition 5, I believe . Sometimes during installation Ubuntu relocate boot code from the boot sector to some other location. Windows may not be be aware of it, bucause GRUB is the one that looks after all these. If you delete partions that belongs to Windows without Windows knowledge, you might see a Hurricane in your Windows World.

---

### Post by vfontanela on 2009-08-31
Wow, it looks like it was a partitio table disorder.

I deleted the last partition (Swap) with Cfdisk, then when I saved it, it recorded the partition table again. Then Ubuntu install was able to see my partitions again.

Thanks everyone.

---

