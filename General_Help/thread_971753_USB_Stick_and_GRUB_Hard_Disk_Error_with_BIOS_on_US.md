---
title: "USB Stick and GRUB Hard Disk Error with BIOS on USB FDD or USB ZIP"
date: 2008-11-05
forum: General Help
---

### Post by linuxvacuum on 2008-11-05
I installed Ubuntu 8.04 on a 1GB USB stick with the Minimal CD. When I reboot the computer with booting option USB ZIP or USB FDD I get ```
GRUB Hard Disk Error
```I then loaded the Live CD, went into GRUB and did :```

device (hd0) /dev/sda
root (hd0,0)
setup (hd0)

```
That computer will only have the USB stick and a DVD drive. 
I even tried grub-install which successfully installed, but I get the same GRUB Hard Disk Error.

Since the BIOS loads GRUB, could it still be a BIOS problem?

---

### Post by linuxvacuum on 2008-11-05
bump

---

### Post by C.S.Cameron on 2008-11-05
On my computer, in BIOS, I need to select the flash drive as first hard disk and not boot from a usb device.
Some older computers will not boot to flash drives.
Usb-creator seems to have problems with some flash drives.

---

### Post by linuxvacuum on 2008-11-05
USB Creator is for live CD. What I want is a normal install but on a USB drive. It is probably that my motherboard is too old.

---

### Post by C.S.Cameron on 2008-11-05
If you are doing a full install to flash drive and using it on a computer that does not boot flash, you can make a boot CD.
The method shown on this page has worked for me:

[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

---

