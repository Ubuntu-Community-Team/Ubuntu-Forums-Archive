---
title: "Problem with Grub Loader?"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by Langr on 2009-04-30
Alright, So when I decided to do a 360 on my Computer, I completely reformatted the 160GB SATA HDD. I wound up installing Linux first using the first ~60GB on the disk and formatted the rest to be FAT32. After installing Linux I chose to install Windows using the last ~100GB Since Windows and it's apps seem to require more HDD space then linux. After installing Windows, I lost my GRUB Loader. So I searched online and restored it using these directions:

sudo grub
find /boot/grub/stage2
root (hd0,5)
setup (hd0)
quit

This allowed me to boot from Linux, the only problem was that Windows now won't be bootable. So I edited the grub and it now the edited part looks like this:

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

title		Windows XP
root		(hd0,2)
savedefault
makeactive
chainloader +1


I think I did this correct. But when I boot the grub loader complains that it is not a partition. When I type SUDO FDISK -L in the terminal it gives me these stats:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x76db6ac8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6709    53890011    5  Extended
/dev/sda2   *        6710       19456   102390277+   7  HPFS/NTFS
/dev/sda5               1        6429    51640879+  83  Linux
/dev/sda6            6430        6709     2249068+  82  Linux swap / Solaris



Any idea as to what is wrong and how I can fix it?

---

### Post by meierfra. on 2009-04-30
Grub starts counting at zero. So you need to use "root (hd0,1)" (not "root (hd0,2)").

---

### Post by Langr on 2009-04-30
Ah, That fixed it. Thank you very much!

---

### Post by meierfra. on 2009-05-01
> **Langr said:**
> Ah, That fixed it.
Good
>  Thank you very much!
You are welcome.

---

