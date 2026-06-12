---
title: "How to put specific and non-specific usb drives in fstab for same device"
date: 2006-10-30
forum: Hardware &amp; Laptops
---

### Post by rrwo on 2006-10-30
I have an external (vfat) USB hard drive and several usb flash drives. I would like to know how (if possible) to configure it so that the specific drive is mounted to one directory, but the flash drives are mounted to generic ones.  Here's what I tried in /etc/fstab

  LABEL=My_Book	/media/My_Book	vfat	user,noauto,rw
  /dev/sdb1	/media/usbdisk0	vfat	user,noauto,rw
  /dev/sdc1	/media/usbdisk1	vfat	user,noauto,rw

It mounts alright, but when I unmount, it says that it's not consistent with fstab. I need to use "sudo umount -f", which defeats the purpose of putting it in fstab.

Is there a way to fix this so that the My_Book drive is always mounted on /media/My_Book but anything else is mounted in usbdisk0 or usbdisk1?

I'm using XUbuntu Edgy 2.6.17-10

---

### Post by rrwo on 2006-10-31
I've figured this out, in part.

I've specified the devices in /etc/pmount.allow:

  /dev/sdb1
  /dev/sdb2

from the command line I use pmount/pumount instead of mount/umount.

In Nautilus (Gnome) I can unmount wihtout being root. In Thunar (Xfce) I'm not given the option to dismount, but that's a different issue.

In /etc/fstab I've specified the My_Book drive as I've like to make sure that it's mouted to a specific location (not necessarily the label).

---

