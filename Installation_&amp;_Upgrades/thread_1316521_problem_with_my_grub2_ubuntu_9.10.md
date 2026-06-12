---
title: "problem with my grub2 ubuntu 9.10"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by blackmarch on 2009-11-06
I use dual boot for my operating system. First, I installed Windows XP, then I install ubuntu 9.10. at first there was no problem with grubloader because there is the option of using Windows XP. after I type the command:

sudo os-prober
sudo update-grub

then the text appears like this in the terminal:

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
done

when i restart my computer, the grubloader doesnt show the windows XP loader............
where's the windows XP?
:(

please help me.....

---

### Post by sliketymo on 2009-11-06
Code:
"sudo fdisk -l"In a terminal (without quotes)and post the output.

---

### Post by blackmarch on 2009-11-06
> **sliketymo said:**
> Code:
"sudo fdisk -l"In a terminal (without quotes)and post the output.

-------------:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc5d969c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1424    11438248+   7  HPFS/NTFS
/dev/sda2            1425        7540    49126770    f  W95 Ext'd (LBA)
/dev/sda3            7541        9376    14747670   83  Linux
/dev/sda4            9377        9729     2835472+  82  Linux swap / Solaris
/dev/sda5            1425        7540    49126738+   7  HPFS/NTFS

---

