---
title: "Dual Boot - Vista exists on 200GB Drive, Acer 5520"
date: 2009-03-08
forum: Installation &amp; Upgrades
---

### Post by IQRules on 2009-03-08
I have an Acer 5520 Laptop, 4GB, 200GB hard drive, AMD Turion TL-58 64x2, 1.9 Ghz Dual core.

Couple questions on Grub and CPU speed.

The partition table is like this now.
1. /dev/sda1 - Vista OS restore, 10G
2. /dev/sda2 - Vista OS Home, 90G
3. unused for 100GB

Should I do manual (expert-level) partition, create a /boot (500M bytes); that sits around at 100GB range from begin cylinder. If I want triple boot with Sun Solaris, what is best way here?

Or just let installer takes over to use the unused disk space.

Should I go to live-CD first and run dd command saving 1st 512 bytys from Master BOOT sector?

And from Live-CD, I got this in /proc/cpuinfo,

# cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : ...
model name      : AMD Turion(tm) 64 Mobile Technology ...
stepping        : ..
cpu MHz         : 800.000   ==== Not 1900.
cache size      : 1024 KB
fdiv_bug        : no
bogomips        : 1593.59 ===== it looks too low here

Thanks

---

### Post by zvacet on 2009-03-08
[Here]("http://ubuntuforums.org/showthread.php?t=724817&highlight=multiboot") is good reference for multiboot.

---

### Post by chubble10 on 2009-03-08
Could try using Wubi

---

### Post by dunkar70 on 2009-03-08
You can only have four primary partitions including one extended partition on each hard drive. You can then divide the extended partition into four logical partitions.

Since two of your primary partitions are already used, you may want to simply install Ubuntu as a primary partition (2-20 GB) and create an extended partition for the remaining space. Place your swap file in the extended partition. This will let you create additional logical partitions in the extended partition to separate (and share) your data from your OS partitions. With 4GB of RAM, you may also want to reduce the "swapiness" of the Ubuntu system. There are posts in the forums to change this.

---

