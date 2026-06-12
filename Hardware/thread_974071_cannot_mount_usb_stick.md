---
title: "cannot mount usb stick"
date: 2008-11-07
forum: Hardware
---

### Post by zeiz on 2008-11-07
I have a computer with old processor K6 III and 256MB mem on Asus mobo (still with 2 ISA slots) and usb on PCI card that was running win2000 sp4 (winXP cannot be installed). Everything was fine but since Ubuntu is my production OS now I decieded to try install of 8.04 on that old machine. 
Install was smooth like 123 (only something about acpi appeared but was fixed without my intervention). I even got 85Hz on that CRT monitor automatically! Looks like Hardy works much faster than win2000! The only problem: usb ports on that card doesn't work :(

I tried:

#lsusb 
no output
# dmesg | grep usb
usbcore: registered new interface driver usbfs
usbcore: registered new interface driver hub
usbcore: registered new device driver usb
usb usb1: configuration #1 chosen from 1 choice
usbcore: registered new interface driver acx_usb
#lshw | grep usb
*-usb
#mount -a 
no output and nothing was mounted (neither usb nor floppy).
#cd /proc/dev/usb -directory exixts.

Maybe I need to edit fstab...but on my production machine it looks the same (no entries with usb). Any help appreciated :)

---

### Post by taurus on 2008-11-07
So when you plug in a USB drive, it doesn't automount for you?  If that's the case, what's the output of this command from a terminal after you've plugged in the USB drive?

```
dmesg | tail
```

---

