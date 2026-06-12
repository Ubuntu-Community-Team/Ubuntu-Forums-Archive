---
title: "[SOLVED] GRUB doesn't detect Vista's partition, can only boot into Ubuntu"
date: 2008-08-11
forum: General Help
---

### Post by Arcanius on 2008-08-11
Hi there, im a complete noob to ubuntu (and linux for that matter). I just finished my new rig, partitioned my HDD so i could install XP/Vista. everything was working, i installed XP first, then vista.

today i decided to install ubuntu, and formatted the partition XP was in,then installed Ubuntu in it. but now i see that on the grub menu, i dont have the option to boot into vista, only Ubuntu is listed. In computer, the windows partition is listed, and shows everything to be there.

my menu.lst (or whatever it's called) says:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       10444    83886592   83  Linux
/dev/sda2   *       16709       38914   178362368    7  HPFS/NTFS
/dev/sda3           10445       11439     7992337+  82  Linux swap / Solaris

Partition table entries are not in disk order

i'd love to not have to install Vista all over again, as i have some important data there, and backups would be a horror

go a bit easy, im a noob at linux, even though im good with windows and computers in general


edit: now, it says that the other partition cannot be mounted :S

in the partition manager of the ubuntu install, i created a swap partition, and tried to resize the vista one, with no success of enlarging it.

---

### Post by logos34 on 2008-08-11
> **Arcanius said:**
> I just finished my new rig, partitioned my HDD so i could install XP/Vista. everything was working, i installed XP first, then vista.

today i decided to install ubuntu, and formatted the partition XP was in,then installed Ubuntu in it. 

bad move.  Your windows boot files were located on sda1, on XP's C:\ drive.  

That's what happens when you install vista after XP--vista takes over the boot process but it detects XP as the 'active' partition and puts the boot files there.

Since you don't want to reinstall vista you'll have to fix the boot somehow from the repair environment on the vista install dvd.

[http://neosmart.net/wiki/display/EBCD/Repairing+the+Windows+Vista+Bootloader](http://neosmart.net/wiki/display/EBCD/Repairing+the+Windows+Vista+Bootloader)

---

### Post by Arcanius on 2008-08-11
I figured that was the problem, after i do this, how would i reinstall Grub? Or should i just use Easybcd to modify the vista bootloader? Thanks a lot, ill get back to you when i fix the whole thing.

PS: how would fixing the bootloader also fix grub, or will it set bootloader as the default booting thing, then i'd boot into vista and fix the bootloader?

---

### Post by logos34 on 2008-08-11
you just want to restore the vista boot manager/files, but if it overwrites grub on the mbr, no prob, just reinstall grub from the live cd (see link my signature).

forgot: afterward you'll need to change the windows entry at the bottom of /boot/grub/menu.lst to point to 'root (hd0,**1**)'

---

### Post by cybrsaylr on 2008-08-11
I had the same problem when first attempting a dual boot setup.
Ubuntu would boot but not XP. It turned out I messed up the size of the partitions and chopped off part of XP.
I had to format all over again to correct the problem.

---

### Post by nacho32 on 2008-08-11
you could download the super grub boot loader ISO then burn to a CD   it has all the tools you need.

---

### Post by Arcanius on 2008-08-11
thanks a lot, i've fixed it, after a few hours of fun:)

now i just have to install grub, and i'll be finished.

now how do i close this topic?

---

