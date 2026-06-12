---
title: "Capture and Deploy Bual-Boot Image"
date: 2008-08-20
forum: General Help
---

### Post by stinky2nine on 2008-08-20
I would like to package Ubuntu to our Windows base image using Wubi simply because I can't find a great solution to be able to capture and mass deploy dual-boot images with ntfs and ext3 partitions.

I created a base image with XP and Ubuntu/Wubi in VMware.  I then captured the base image.  I ran sysprep in XP before I captured the image.

I then tried to restore the base image to another VMware instance.  XP part works perfect, but Ubuntu is not.

I am getting this error during boot:

```
Check root= bootarg cat /proc/cmdline
or missing modules. devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/F05865AF5865756E does not exist. Dropping to a shell.

```

I guess the problem is that it's trying to mount the disk by using uuid and not direct /dev/sd path.

Has anyone overcome with this issue?

Does Wubi support silent installation with package selection support?

---

### Post by stinky2nine on 2008-08-20
Found a solution - ugly but works...  Modified /boot/grub/menu.lst and set root=/dev/sda1.  Not a pretty solution.

---

