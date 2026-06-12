---
title: "GRUB not detecting SATA drives when USB drive attached"
date: 2007-02-05
forum: Hardware &amp; Laptops
---

### Post by mrwilloby on 2007-02-05
I tried searching on these forums and elsewhere before posting, but no one seems to have the same problem.

[This post]("http://ubuntuforums.org/showthread.php?t=185697") seemed to almost help, but it wasn't quite the same.

I have one IDE drive with two partitions which is not a problem at all.  Windows and a data partition reside there. /dev/hda

I have two internal SATA drives connected to the motherboard.  Ubuntu resides on the second partition of the first drive.

I have an external USB hard drive with openSUSE installed on the second partition.

And where the problem arose is when I switched a second external hard drive from a USB connector to an eSATA connector.  Apparently the eSATA drive gets read before the motherboard-based SATA drives, so the eSATA drive is now /dev/sda.

No problem, right?  Just redo the menu.lst file.  It didn't quite work that way.

When all of the drives are plugged in GRUB is no longer able to see the internal onboard SATA drives.  I confirmed this by playing with the Super Grub Disk and by turning on the computer with the external USB drive turned off.  When the USB was turned off, the Ubuntu partition was detected under /dev/sdb2 as expected.  When the USB drive was turned back on, GRUB thinks the USB drive is (hd2,1) and loads the /boot/grub/menu.lst file from the openSUSE installation.  This would work fine by editing that file as well.  The problem is that since GRUB does not recognize the internal SATA drive at that point, when I select the entry for Ubuntu it cannot find the kernel file because it's not actually loading that partition.

It's driving me mad.  I'd rather not switch the eSATA back to a USB connection because I like the speed gain and I don't really want to wipe the openSUSE installation to see what would happen.

Any ideas?

---

