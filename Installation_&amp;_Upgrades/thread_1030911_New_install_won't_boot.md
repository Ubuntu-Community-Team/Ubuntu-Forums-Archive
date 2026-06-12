---
title: "New install won't boot"
date: 2009-01-04
forum: Installation &amp; Upgrades
---

### Post by MikeBenza on 2009-01-04
I've tried to do a new install on a brand new machine of 8.04.1.  I've tried it many times with many different tweaks.  Basically, I'm doing the next-to-simplest install possible: GUI installer with everything standard, but with an extra partition for home and one for a virtual raid device I'm going to add once the machine works.

So, I go through the installation process, it says to take out the CD and restart.  I do that.  When it restarts, the machine won't boot.  It just goes to a blank screen (which is what it did before the install too).

If I insert the installer CD and choose "Boot from first hard drive", it boots fine.

Here is the output from fdisk -l:
```


Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000f2beb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2            2433        6079    29294527+  83  Linux
/dev/sda3           29916       30401     3903795   82  Linux swap / Solaris
/dev/sda4            6080       29915   191462670   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e2629

   Device Boot      Start         End      Blocks   Id  System


```I tried running grub-install once I booted from first hard drive using the install cd (sudo grub-install /dev/sda), but that didn't work either.

If it helps, the mobo is an ASUS P5N-MX.

Please figure out how to make this thing boot.

---

### Post by MikeBenza on 2009-01-04
A quick update:

If I run grub:
```

grub> root (hd0,0)

Error 21: Selected disk does not exist

grub> find /boot/grub/stage1

Error 15: File not found

grub> find 'boot/grub/stage1'

Error 15: File not found

```


And the contents of my /boot/grub/device.map file:
```

(hd0)    /dev/sda
(hd1)    /dev/sdb

```

---

### Post by MikeBenza on 2009-01-06
*bump*

Anyone?

---

### Post by Rithmarin on 2009-01-07
I'd hazard a guess that the hard drive with linux on it isnt set as first hard drive to boot from in the bios?

I'd expect to see an error message like Operating system not found or grub 22 error if it was trying to access your hard drive and the mbr was bad. The fact that you can boot from hard disk when selected from the cd menu suggests that the install is ok.

---

### Post by MikeBenza on 2009-02-12
Woohoo...finally figured it out.  In the BIOS, there's an option in the boot section called "Hard Disk Priority."  The second disk was selected instead of the first...As soon as I switched it, the machine booted right up.

---

