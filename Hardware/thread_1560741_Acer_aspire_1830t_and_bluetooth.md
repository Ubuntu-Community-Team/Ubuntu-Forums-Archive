---
title: "Acer aspire 1830t and bluetooth"
date: 2010-08-25
forum: Hardware
---

### Post by past on 2010-08-25
Good day, I bought a laptop like this one [https://help.ubuntu.com/community/Aspire1830T](https://help.ubuntu.com/community/Aspire1830T). But with bluetooth, which was clearly visible and functioned until the laptop was win7.
Staged 10.04 - no bluetooth. Neither lsusb nor rfkill list, nor with
loaded with acer-wmi either with unloaded, on all available cores, even
on the linux-image-2.6.35-020635rc1-generic.

I can not understand on what package bug reports to write?
At the kernel, at rfkill, on bluetooth?
Sorry for my google translated english.

---

### Post by past on 2010-08-25
I found that after double-clicking FN-F3 (off and on all wireless devices), the adapter appears for a short time.
Here is part of dmesg:
[  392.842291] usb 1-1.4: new full speed USB device using ehci_hcd and address 7
[  392.962895] usb 1-1.4: configuration #1 chosen from 1 choice
[  393.215198] usb 1-1.4: USB disconnect, address 7
[  394.631159] usb 1-1.4: new full speed USB device using ehci_hcd and address 8
[  394.742338] usb 1-1.4: configuration #1 chosen from 1 choice
[  394.910438] usb 1-1.4: USB disconnect, address 8
[  394.910477] btusb_intr_complete: hci0 urb ffff88011b18d540 failed to resubmit (19)
[  394.913766] btusb_bulk_complete: hci0 urb ffff88011b18d6c0 failed to resubmit (19)
[  394.917326] btusb_bulk_complete: hci0 urb ffff88011b18d0c0 failed to resubmit (19)
[  438.894962] usb 1-1.2: new full speed USB device using ehci_hcd and address 9
[  438.974917] usb 1-1.2: device descriptor read/64, error -32
[  439.987526] usb 1-1.2: configuration #1 chosen from 1 choice
[  440.370532] Bluetooth: RFCOMM TTY layer initialized
[  440.370549] Bluetooth: RFCOMM socket layer initialized
[  440.370558] Bluetooth: RFCOMM ver 1.11

---

