---
title: "Problem mounting CD-ROM drive"
date: 2007-03-25
forum: Hardware &amp; Laptops
---

### Post by Jc1991 on 2007-03-25
My CD drive has stopped auto-mounting after my recent switch to 6.10.

/etc/fstab is still set to mount /dev/hdc to /media/cdrom0, but nothing happens when I insert a disk.
What options would I need to append to "mount /dev/hdc /media/cdrom0" to correctly mount the drive manually?

Thanks in advance for any help.

---

### Post by s0cket on 2007-03-26
You *should* need no options.  Linux mount command in most cases will autodetect everything else it needs to mount (fs type, etc).

If I'm not mistaken I believe that having your CDROM in fstab is unessacary.  HAL and Gnome should detect when you insert a disc and mount the drive for you.  Try this to see if gnome-mount is having a problem:

gnome-mount -vtd /dev/hdc

---

### Post by Jc1991 on 2007-03-26
Completely forgot to mention, I'm not using Gnome. I'm using Xfce 4. Sorry.

---

### Post by s0cket on 2007-03-26
This is just a guess but you might want to look into autofs.

---

