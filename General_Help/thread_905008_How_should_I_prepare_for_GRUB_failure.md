---
title: "How should I prepare for GRUB failure?"
date: 2008-08-29
forum: General Help
---

### Post by 3pinner on 2008-08-29
I have a dual boot configuration, using GRUB to choose which OS I want to use.
I haven't had a single problem with this setup, but we are talking computers here, and I would like to know how I can prepare for potential future problems if GRUB gets corrupted, or fails for some reason.

Thanks!

---

### Post by quibbler on 2008-08-30
> **3pinner said:**
> I have a dual boot configuration, using GRUB to choose which OS I want to use.
I haven't had a single problem with this setup, but we are talking computers here, and I would like to know how I can prepare for potential future problems if GRUB gets corrupted, or fails for some reason.

Thanks!
You could go here: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Download the iso file and burn it. Read the documentation.

Regards quibbler

---

### Post by cdtech on 2008-08-30
You could store your GRUB bootloader image to a USB stick in case you need to restore it:
```
sudo dd if=/dev/sda of=/media/usb-pen/GRUB.image bs=446 count=1
```
To restore the GRUB bootloader just reverse the command:
```
sudo dd if=/media/usb-pen/GRUB.image of=/dev/sda bs=446 count=1
```

---

