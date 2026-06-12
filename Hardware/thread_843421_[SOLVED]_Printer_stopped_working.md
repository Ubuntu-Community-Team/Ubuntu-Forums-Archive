---
title: "[SOLVED] Printer stopped working"
date: 2008-06-28
forum: Hardware
---

### Post by richtl on 2008-06-28
My HP 722C worked yesterday. This morning I got a bunch of updates, including a new kernel (2.6.24-19). Today it no longer prints. In fact, the Printer Manger doesn't even see that the printer exists. Here's what I see in /var/log/messages when I plug it in:

Jun 28 11:07:25 cacao kernel: [  194.691088] usb 1-2: new full speed USB device using uhci_hcd and address 5
Jun 28 11:07:25 cacao kernel: [  194.779799] usb 1-2: configuration #1 chosen from 1 choice
Jun 28 11:07:25 cacao kernel: [  194.792067] usblp0: USB Bidirectional printer dev 5 if 0 alt 1 proto 2 vid 0x067B pid 0x2305

Tried gnome-cups-manager. It doesn't see the printer either.

---

### Post by AlexBellisBrown on 2008-06-28
Just to make sure it is the new Kernel, could you boot into an old one? Restart your computer, and press ESC to bring up the boot menu, select an older kernel, and boot into it, then try your printer. Let us know what happens.

---

### Post by richtl on 2008-06-29
You're right. It fails with the older kernel as well. I noticed the following in the cups error log:

E [29/Jun/2008:15:12:08 -0400] PID 7354 (/usr/lib/cups/daemon/cups-driverd) crashed on signal 9!

Don't see any other new packages that would obviously affect printing.

---

### Post by starcannon on 2008-06-29
Try grabbing and reinstalling all the hplip packages in synaptic package manager, then go to System-->Administration-->Printing and try reinstalling the printer. Thats where I'd start off anyway.

GL let us know how it works out.

---

### Post by richtl on 2008-06-30
I completely uninstalled and reinstalled hplip and hplip-data. The Printer tool still doesn't see the local printer.

I see the following in /var/log/debug

Jun 30 00:09:59 cacao NetworkManager: <debug> [1214798999.484918] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2305_noserial'). 
Jun 30 00:09:59 cacao NetworkManager: <debug> [1214798999.522608] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_67b_2305_noserial_if0'). 

Any other places I can look for clues?

---

### Post by richtl on 2008-07-03
The latest update fixed the problem. It prints again :-)

---

