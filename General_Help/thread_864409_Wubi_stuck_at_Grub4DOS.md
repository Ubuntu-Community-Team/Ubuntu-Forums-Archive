---
title: "Wubi stuck at Grub4DOS"
date: 2008-07-19
forum: General Help
---

### Post by sciurus on 2008-07-19
Hi,

I'm working on a system with 4 hard drives mapped as the following by Windows.

Disk 0 - C: & D:
Disk 1 - E:
Disk 2 - F:
Disk 3 - G:

I've tried installing Ubuntu to drive 3 using Wubi 505 and 506. When I reboot to complete the install, I'm dropped to a grub4dos prompt. grub4dos can't find the menu file.

> 
find /ubuntu/install/boot/grub/menu.lst
Error 15: File not found


If I try to switch the root device to the drive with Wubi, it fails.

> 
root (hd3,0)
Error 25: Disk read error


I can switch to (0,0), (0,1), (1,0), and (2,0). without incident. Drive 2 and 3 are the same model. The filesystem on G: is defragmented and passes chkdsk. Logs will be posted below. Any thoughts?

---

### Post by sciurus on 2008-07-19
Logs.

---

### Post by tinybit on 2008-07-20
Most possibly the BIOS lost the ability to access your (hd3).

You may try to install ubuntu on other drives. Or you may at least copy your menu.lst and vmlinuz-* and initrd* files on a drive that GRUB(and BIOS) can access, and then reboot and continue the booting or installing process.

---

