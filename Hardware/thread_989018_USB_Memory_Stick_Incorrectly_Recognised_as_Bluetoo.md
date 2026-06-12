---
title: "USB Memory Stick Incorrectly Recognised as Bluetooth Device in Hardy"
date: 2008-11-21
forum: Hardware
---

### Post by ckwright@allmail.net on 2008-11-21
When plugged my memory stick with usb code 0c10:0000 (as given by lsusb) leads to the dmesg lines

[  936.206581] usb 2-2: new full speed USB device using uhci_hcd and address 2
[  936.376696] usb 2-2: configuration #1 chosen from 1 choice
[  937.314417] Bluetooth: HCI USB driver ver 2.9
[  937.317175] usbcore: registered new interface driver hci_usb


The gnome usb icon is activated and shows no devices under 'Select device to browse'.

The uname -a output is
Linux evesham 2.6.24-21-generic #1 SMP Tue Oct 21 23:43:45 UTC 2008 i686 GNU/Linux

My first attempt to solve this is try to find a simple configuration fix to block the incorrect bluetooth recognition in the hope that the system then recognises the device it as a mass storage device. But finding the appropriate documentation seems a heavy task!

---

### Post by ajgreeny on 2008-11-21
If you have any files you need on the usb stick, try booting without bluetooth enabled, (you can do that by using BUM, boot up manager).  If that doesn't work, or you have no files you need on the stick, what about reformatting using gparted.  Very weird, nonetheless!  What, if anything, do you think is on it?

---

### Post by ckwright@allmail.net on 2008-12-20
I have to apologise for this! I mistakenly picked up the wrong device when hurriedly leaving home - so this is a non-problem - nothing wrong except me!

---

