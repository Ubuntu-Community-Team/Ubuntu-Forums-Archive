---
title: "2TB Partition Limit - How?"
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by wbell on 2009-02-12
Okay, I learned "the hard way" that "msdos" labeled drives and fdisk have a 2.0TB partition limit.  I also found a great partitioning utility called **[Parted Magic]("http://www.partedmagic.com/")**, which would allow me to create a "gpt" labeled drive that will allow the creation of partitions greater than 2.0TB.

**My Question:** How do I install Ubuntu Server v8.10 on a GPT-labeled drive?

If I manually create my partitions with Parted Magic, then use the Ubuntu Server install disk to perform only the installation, it always fails on the GRUB install.

If I try to let Ubuntu create and format the partitions, it freezes at 33% on the creation of the "/" partition.

PLEASE HELP!


My current system has a 3ware hardware RAID controller, with five (5) 1.0TB SATA drives, in a RAID5 configuration.  It produces ~4.0TB of space.

---

### Post by wbell on 2009-02-12
Well...  The installer finally made it past the 33%, however it fails on boot.

I have something else I'm going to try...

---

### Post by mttman on 2009-02-12
Hello,

I've never really done anything with servers or raid, but I would think the best thing for you to do is to either break up your one big partition and just mount a large one where your going to have large files and another where the rest of your stuff will be, or to try a new partition type. 
EX - ReiserFS instead of ext3.
I'm not sure what the limits on partition size are for these file system but it would be worth looking up if you have to have one abnormally giant partition for your business needs.

Hope this helps

<Mttman>

---

### Post by caljohnsmith on 2009-02-12
To my knowledge Grub does not support GPT. I agree with mttman that probably the best thing to do is break your partitions down in to more manageable sizes.

---

### Post by dean123 on 2009-02-13
You can't boot from a 2TB+ array. Use 3ware bios utility to create a boot volume while creating your big array. Install Ubuntu on the boot volume. Format the rest after booting into Ubuntu. Hope that helps.

---

