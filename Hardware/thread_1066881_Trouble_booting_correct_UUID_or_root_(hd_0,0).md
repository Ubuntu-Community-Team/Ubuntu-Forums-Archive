---
title: "Trouble booting correct UUID or root (hd 0,0)"
date: 2009-02-11
forum: Hardware
---

### Post by MaindotC on 2009-02-11
I installed 8.10 to a usb drive via the live cd.  When I try booting from the usb drive, I get a message stating something like:
```

ALERT! /dev/disk/by-uuid/<uuid> does not exist!
Gave up waiting for device
Boot args (cat/proc/cmdline)
Check rootdelay - did the system wait long enough?
Check root - did the system wait for the right device?

```
and drops me into the initramfs prompt.
I tried changing the rootdelay to 120 per [this thread](http://ubuntuforums.org/showthread.php?t=981159) and then I tried changing [menu.list and device.map per this thread](http://ubuntuforums.org/showthread.php?t=947777).  I changed device.map from:
```

(hd0)     /dev/sda

```
to
```

(hd0)    /dev/sda1
and
(hd0)   /dev/sdb

```
but the same problem happened.  I went into menu.lst and changed
```

title           Ubuntu 8.10, kernel 2.6.27-7-generic
uuid          16a4e1e4-26c9-43bb-bfe9-670c1ad9c1c5
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=UUID=16a4e1e4-26c9-43bb-bfe9-670c1ad9c1c5
initrd          /boot/initrd.img-2.6.27-7-generic
quiet

```
to
```

title           Ubuntu 8.10, kernel 2.6.27-7-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=UUID=16a4e1e4-26c9-43bb-bfe9-670c1ad9c1c5
initrd          /boot/initrd.img-2.6.27-7-generic
quiet

```
and that yielded the same result.

What I'm concerned with is when I view the contents of blkid now, with my regular system booted, it says:
```

/dev/sda1: UUID="1ba32785-e91c-4d20-a7d6-4eb09379d8a4" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="5b4614d9-0d9a-4a53-8c7b-a609a7b6bbde" 
/dev/sdb1: UUID="16a4e1e4-26c9-43bb-bfe9-670c1ad9c1c5" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="8eafc852-76c5-457b-9037-58a6ce37638d"

```
When I boot from the USB drive, how do I know it considers itself /dev/sda and not /dev/sdb ?  Is there something I can do in initramfs to determine what /dev it is?

---

### Post by MaindotC on 2009-02-14
bump

---

### Post by Yashiro on 2009-02-14
> root=UUID=UUID=16a4e1e4-26c9-43bb-bfe9-670c1ad9c1c5
root=UUID=16a4e1e4-26c9-43bb-bfe9-670c1ad9c1c5

---

