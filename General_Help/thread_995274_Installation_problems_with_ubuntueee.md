---
title: "Installation problems with ubuntueee"
date: 2008-11-27
forum: General Help
---

### Post by jspolen on 2008-11-27
Hi just recently bought a asus eeepc 900 and been trying to install ubuntueee. Been sitting a couple of days now with no luck.

I can boot up from my usb and the installation starts. But somewhere at the end of my installation I get pushed into the usb live version of ubuntueee. I can see that ubuntu is installed on my ssd drive, but not flagged bootable.

So I naturally flag it bootable and reboot my computer. But now I  get 99 all over my screen. I can boot from usb but not from the computers harddrive.

Ok then I thought. Maybe I should install grub on my MBR. ran these commands in the usb live version:
grub
root (hd0,0)
setup (hd0)

After my bios screen shows it displays a black screen for a millisecond just to go back to the bios screen. And so it goes...

this is my output from fdisk -l
[I]Disk /dev/sda: 16.1 GB, 16139354112 bytes
255 heads, 63 sectors/track, 1962 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x36473646

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1874    15052873+  83  Linux
/dev/sda2            1875        1962      706860    5  Extended
/dev/sda5            1875        1962      706828+  82  Linux swap / Solaris

Disk /dev/sdb: 1031 MB, 1031798272 bytes
32 heads, 62 sectors/track, 1015 cylinders
Units = cylinders of 1984 * 512 = 1015808 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1015     1006849    b  W95 FAT32
[/I]

Does anyone have a clue what's going on here???

---

