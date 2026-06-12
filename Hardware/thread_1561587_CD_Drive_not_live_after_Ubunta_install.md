---
title: "CD Drive not live after Ubunta install"
date: 2010-08-26
forum: Hardware
---

### Post by muddyfox on 2010-08-26
Had a problem with a 6 year old notebook resulting in loss of XP Home OS. Replaced it with Ubunta - well impressed!

However, the CD drive is not live any more (it was fine when used for install) - any suggestions please.

---

### Post by sikander3786 on 2010-08-26
You mean it doesn't work properly or it is not showing up in "Computer"?

---

### Post by muddyfox on 2010-08-26
Thanks for the reply sikander, 

Since the install - a couple of weeks ago now the CD Drive has not been visible in places / computer

Nor has any USB memory keys been visible. Today though, on boot, the USB drive I had plugged into a USB is there and I can read data from it. 

On a reboot after an unsuccessful attempt to load Winestall the desktop icon for the CD Drive appeared but both through trying to open the drive of through eject it's not working.

> **sikander3786 said:**
> You mean it doesn't work properly or it is not showing up in "Computer"?

---

### Post by sikander3786 on 2010-08-27
Did you see in your Computer's Bios? Is the CD-ROM Drive being identified there? Also did you check for any hardware fault? Try pausing at the Bios and ejecting the tray through the drive eject button. Is it functioning?

Also post /etc/fstab file.

```

cat /etc/fstab

```

For the USB mount problem, after inserting your USB, type in a terminal

```

lsusb

```

And post the output.

---

### Post by muddyfox on 2010-08-28
Thanks - not sure I did it right but here is the output:

cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=84d8120b-3c3d-40c8-9d51-f0998d4626b1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=28241250-5766-48b7-95a1-9e00fb8839a4 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
geoff@ubuntu:~$

---

