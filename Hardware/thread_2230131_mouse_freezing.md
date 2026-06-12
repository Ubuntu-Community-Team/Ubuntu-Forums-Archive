---
title: "mouse freezing"
date: 2014-06-17
forum: Hardware
---

### Post by rubing on 2014-06-17
Hi all!  

I have standard 32 bit ubuntu 14.04 installed on my desktop which is AMD Phenom(tm) 9850 Quad-Core Processor × 4 with 3.7 GiB memory and GeForce 8300/integrated/SSE2/3DNOW! Graphics card.

The problem I am having is that my mouse keeps freezing.  Typical scenario is that it works fine for the first 15 minutes to hour after starting the computer, but at some point will stop working.  I will need to restart the computer in order to get the mouse working again.  If I plug mouse into another USB port that doesn't seem to help.  Help appreciated.

---

### Post by QIII on 2014-06-17
Hello!

You may want to let everyone know the OEM and model of the mouse to look for common hardware issues.

Do you have another mouse handy to check to see if it works?  Rule out a hardware fault first.

---

### Post by rubing on 2014-06-17
I have tried several mice and they all yield the same problem.  The one I am using now is a DELL mouse with cord that came with my Dell Laptop.  I have a keyboard with trackball on it, that seems to stay working even if the mouse fails.  I typed dmesg on the console after my mouse failing and found this message last:

[   61.179311] usb 2-5: reset high-speed USB device number 4 using ehci-pci

---

### Post by rubing on 2014-06-17
I edited /etc/modprobe.d/blacklist.conf and removed the defualt comments to blacklist usbmouse and usbkeyboard.  Seems to have stopped freezing.

---

