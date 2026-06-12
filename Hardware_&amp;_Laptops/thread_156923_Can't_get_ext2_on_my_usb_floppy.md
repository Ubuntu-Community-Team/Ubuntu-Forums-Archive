---
title: "Can't get ext2 on my usb floppy"
date: 2006-04-08
forum: Hardware &amp; Laptops
---

### Post by nathan_n on 2006-04-08
I was reading through the forums to try to figure this out on my own but I'm having problems getting things to work right.  I am currently using a sony USB floppy drive which I can access through my desktop and see in the /media/floppy directory.  However, I want to mount a new ext2 filesystem on the disk and I'm having trouble doing it.  I'm trying to do this:

root@Nathan:/# mkfs /media/floppy 1440
mke2fs 1.38 (30-Jun-2005)
/media/floppy is not a block special device.
Proceed anyway? (y,n) y
mkfs.ext2: Filesystem larger than apparent device size.
Proceed anyway? (y,n> y
/media/floppy: Is a directory while setting up superblock.

I don't know if I'm having a problem because I'm doing this wrong or because it's a USB drive.  I tried the sudo version, and also tried to edit the /def/fstab file for /dev/fd0 /media/floppy0 ...etc that was in another post that I found dealing with mounting floppies.  Can anyone help me with this?  Thanks. :)

note:

never mind. I was looking in the wrong area. needed to mount /dev/sda not /media/floppy. Sorry for the inconvience.  I can't figure out how to delete this message.  Can a mod do this for me?  Thanks guys.

---

### Post by hajk on 2006-04-08
You can't run the mkfs command on a mounted partition...

So, find out what the real device name is for the USB floppy, probably something like /dev/sdb (the letter "b" could also be "a" or "c", depending on other devices on your computer). Assuming that it is /dev/sdb, you should first run the "sudo fdisk /dev/sdb" command, and get a listing of the partitions with "p". It will probably show something like /dev/sdb1 with a FAT32 or W95 filesystem -- you can then delete this partition with "d", followed by making a new one with "n".
Quit and save the partition table with "w".

Now, "sudo mkfs -t ext2 -p -v /dev/sdb1" will install the ext2 filesystem.

N.B. You don't actually need a partition (like sdb1), you could also install the ext2 filesystem on the whole device /dev/sdb (mkfs will query you about this, but it's OK).

Finally, there should be an entry in /etc/fstab linking this device to the /media/floppy mount point that you already have.

Have fun!

---

