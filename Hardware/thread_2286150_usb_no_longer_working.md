---
title: "usb no longer working"
date: 2015-07-10
forum: Hardware
---

### Post by ling.ja on 2015-07-10
Hello. I'm new here, so i hope I'm posting in the right place.

My usb ports stopped working. This happened before, but a reboot always fixed the problem. This is no longer the case.
Can someone help me?

My hardware: HP probook 450
OS: Ubuntu 14.04

Observations when using an usb-stick with power indicator:
When plugging in the usb-stick, the power indicator flashes for a moment, and then turns off.
When rebooting while the usb-stick is plugged in, the power indicator turns on for most of the booting process, and then turns off before the login screen shows.

What I tried:
I followed the instructions found in this post to disable usb autosuspend: [URL="http://askubuntu.com/questions/526082/2-usb-ports-stopped-working"]http://askubuntu.com/questions/526082/2-usb-ports-stopped-working
[/URL]
lsusb:
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


EDIT:
A part of my dmesg file, might help?

[   18.938681] usb 3-12: Device not responding to set address.
[   19.142791] usb 3-12: device not accepting address 7, error -71
[   19.254943] usb 3-12: new full-speed USB device number 8 using xhci_hcd
[   19.272092] usb 3-12: New USB device found, idVendor=0cf3, idProduct=311f
[   19.272094] usb 3-12: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[   20.320082] xhci_hcd 0000:00:14.0: xHCI host not responding to stop endpoint command.
[   20.320085] xhci_hcd 0000:00:14.0: Assuming host is dying, halting host.
[   20.320106] Bluetooth: hci0 urb ffff88013548ba80 failed to resubmit (22)
[   20.320144] Bluetooth: hci0 urb ffff8801354b9840 failed to resubmit (22)
[   20.320176] Bluetooth: hci0 urb ffff8801354b93c0 failed to resubmit (22)
[   20.320206] xhci_hcd 0000:00:14.0: HC died; cleaning up
[   20.320251] usb 3-2: USB disconnect, device number 2
[   20.320898] usb 3-5: USB disconnect, device number 3
[   20.321080] usb 3-6: USB disconnect, device number 4
[   20.322322] usb 3-7: USB disconnect, device number 5
[   20.348266] usb 3-12: USB disconnect, device number 8

EDIT 2:
Ok, now I'm confused. Re-starting the laptop with an android phone plugged in (usb debugging activated) fixes the problem with all usb ports (not just the one where the phone is plugged in), a normal usb stick does not work. Re-starting the laptop without the phone plugged in causes the problem to come back.

---

### Post by sudodus on 2015-07-10
Welcome to the Ubuntu Forums :-)

Maybe there is some problem with the USB pendrive, maybe there is a hardware problem in the computer, maybe there is a problem with the installed Ubuntu system. Some testing might help you localize the problem.

Does it work in another computer?

Does your computer work with another pendrive?

What happens if you boot your computer from a live drive (a DVD disk or USB pendrive with Ubuntu)?

---

### Post by ling.ja on 2015-07-10
> **sudodus said:**
> 

Does it work in another computer?

Does your computer work with another pendrive?

Thank you for answering.
-The pendrive works with another computer (and with my laptop, after the temporary fix mentioned in edit 2)
-The computer does not work with other pendrives (or any other type of usb device) until I use the temporary fix mentioned in edit 2.
-Live drive not tested, I will try this later (but can't do this within the next few hours, as I'm currently not at home).

My guess: For some reason, my pc shuts down the usb ports at startup, unless there is a device plugged in that tells it not to do this.

---

### Post by sudodus on 2015-07-10
We can continue the trouble-shooting when we know how the USB system works when the computer is booted from a live drive.

---

