---
title: "can't mount raid0 anymore"
date: 2008-11-03
forum: General Help
---

### Post by axelman on 2008-11-03
Hi everyone.

After an involuntary hard reset, it seeems I'm unable to mount my two RAID0 partitions anymore.

I've two identical HDs (sda and sdb), both with 4 partitions:
/dev/sda1 (ext3, /boot)
/dev/sda2 & sdb2 (soft raid, swap)
/dev/sda3 & sdb3 (soft raid, ext3, /)
/dev/sda4 & sdb4 (NTFS, used in Win)

Windoze recognizes both drives, mounts the NTFS partitions and they work right.


When starting ubuntu and after a few seconds of splash image (ubuntu loading) I recieve the following message:

Boot from (hd0,0) ext3 (lots of hexadecimal stuff)
Starting up...
Gave up waiting for root device. Common problems:
(something about missing drivers, which aren't really missing)
ALERT! /dev/md2 does not exist. Dropping to a shell!

And then i get dropped to a shell (initramfs) with lots of missing commands.

If I ls /dev, I can clearly see /dev/md1 and /dev/md2, and typing:
mdadm --detail /dev/md2 (or md1)
I get the correct information on RAID configuration and devices.

However, I can't mount md1 nor md2.

Is it that md2 filesystem is corrupt? Is there any way to fix it?
By the way, I can mount /dev/sda1 and edit grub's menu.cfg, and everything seems OK.

Thanks a lot for your help.

---

### Post by fjgaude on 2008-11-03
Did you create this system, the arrays?

If /dev/sda has some kind of failure everything else is in trouble, maybe.

You run Windows through the grub menu?

---

### Post by psusi on 2008-11-03
Can you post the exact output of mdadm --detail?  Also what do you mean you can't mount it?  How did you try and what exactly happened?

---

