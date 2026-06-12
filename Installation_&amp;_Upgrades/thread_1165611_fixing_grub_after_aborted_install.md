---
title: "fixing grub after aborted install"
date: 2009-05-20
forum: Installation &amp; Upgrades
---

### Post by mnielsen1984 on 2009-05-20
I was going to install another version of Linux, but decided against it, but the grub must have gotten corrupted already.  The hard drive hasn't been over written, so I believe that Ubuntu is still on there.

I have Ubuntu 8.10 on there, and am currently using the live CD for it.  I found [this discussion]("http://ubuntuforums.org/showthread.php?t=224351") on how to fix the grub.  When I get into the grub using terminal, I type 'find /boot/grub/stage1'. but I get an error message that says 'Error 15: File not found.'

Is there a way to ressurrect the grub?

Thanks,
mnielsen1984

---

### Post by utnubuuser on 2009-05-20
When you install Ubuntu, install with a seperate /home partition so you can simply re-install OS without over-writing settings/documents.

suppose you tried: sudo grub>>find /grub/stage1 instead of /boot/grub...

---

### Post by mnielsen1984 on 2009-05-22
OK, I installed a another version on a smaller part, but its still not seeing the first installation.  Is everything lost now?

---

### Post by utnubuuser on 2009-05-23
Hi - If you start gParted, do the other partitions show up in the listing?

(You might have to install gParted since it's a fresh install.)

And if the old OSs partitons are listed, note their numbers. ie. sda1, sda2, etc, because you might have to make entries for them in fstab.  Again, fstab, in a terminal, is: > sudo gedit /etc/fstab

This is my fstab listing for my home partition:> # /dev/sda9
UUID=7e6fa301-8433-444f-9fae-d02ef90b003b /home           ext3    relatime        0       2You can probably change the UUID info and /dev/sda9 listing so it matches the partition info from your hdd.

To get UUID info, in terminal do:> sudo blkid- that info is from a 8.04 install, if you're using a different version, the listings might look slightly different.

You also have to make an actual mount-point for the partition you're trying to access.
Again, in terminal:> sudo mkdir /dev/sdaX(change sdaX to the correct number for your partition).

Then either restart, or, in terminal: sudo mount /dev/sdaX

---

