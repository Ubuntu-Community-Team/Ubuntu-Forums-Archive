---
title: "USB Sound Card Disconnects On Use"
date: 2015-12-17
forum: Hardware
---

### Post by JonoBNZ on 2015-12-17
Hey all,

I've just recently upgraded from 15.04 to 15.10 and my USB sound card/mixer has stopped working.

This is Ubuntu with Mate, if that's worth knowing.  15.04 was a fresh install with an in-place upgrade to 15.10.  The hardware is an Intel NUC5i5RYH Mini-PC.

The USB sound hardware is a E-MU 0202 USB Sound Card/Mixer.  It has worked perfectly since I bought it (12.04) and worked on this hardware under 15.04.

The way the problem manifests is that when I plug the USB device in, the power LED lights up on the front and the device appears to enumerate correctly, judging by the kernel messages pasted below.  After about ten seconds the power LED goes out, but there are no further kernel messages.  I can see the device listed as a hardware device in the volume control applet thing and as an option for sound input/output under the respective tabs.  If I try set it as an output device and play anything to it, or use the test speakers function then the device disappears from the listings and I get the kernel message that the USB device has disconnected, followed by the device enumerating again with a new device number.  The power LED comes back on for 10 seconds and then goes out again.

> [   20.028146] usb 1-1.4: new high-speed USB device number 8 using xhci_hcd
[   20.130335] usb 1-1.4: New USB device found, idVendor=041e, idProduct=3f02
[   20.130339] usb 1-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   20.130341] usb 1-1.4: Product: E-MU 0202 | USB
[   20.130343] usb 1-1.4: Manufacturer: E-MU Systems, Inc.
[   20.130345] usb 1-1.4: SerialNumber: E-MU-CD-3F02-07D90915-1302F-8740T2A
[ 1493.437043] usb 1-1.4: USB disconnect, device number 8
[ 1493.682041] usb 1-1.4: new high-speed USB device number 9 using xhci_hcd
[ 1493.784621] usb 1-1.4: New USB device found, idVendor=041e, idProduct=3f02
[ 1493.784624] usb 1-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1493.784626] usb 1-1.4: Product: E-MU 0202 | USB
[ 1493.784627] usb 1-1.4: Manufacturer: E-MU Systems, Inc.
[ 1493.784628] usb 1-1.4: SerialNumber: E-MU-CD-3F02-07D90915-1302F-8740T2A

This shows a fresh boot and then after a few minutes the output device being set to the E-MU 0202 and a song being played, at which point the audio comes out of the front speaker jack instead of the USB sound card and the device appears to disconnect.

So far I've tried different ports (front and back of the device, USB 2.0 and USB 3.0 ports), as well as shifting the device onto a powered USB hub and unplugging everything else that was on the USB, aside from the keyboard/mouse.  I've also tried the sound card on a different PC to make sure it's not a hardware issue.

I've spent quite a few hours searching around but can't for the life of me find anything even remotely useful for debugging USB devices or issues with them.  I'm not even sure where I should be looking for any further information, so I'd really appreciate any suggestions.

---

### Post by deepakdeshp on 2015-12-18
Grub gives option to boot from your old kernel when you boot from recovery mode . Boot from your old kernel and try.


Otherwise please try installing latest Kernel. It may support the card. But [COLOR=#ff0000]it may break[/COLOR] the system if some vital hardware isnt supported.

[http://www.ubuntumaniac.com/2015/11/how-to-upgrade-to-linux-kernel-43.html](http://www.ubuntumaniac.com/2015/11/how-to-upgrade-to-linux-kernel-43.html)

---

### Post by JonoBNZ on 2015-12-18
Hi deepakdeshp,

Thanks for the quick response.

I just tried both booting into the old kernel (3.19) where it worked, as well as installing 4.3 according to those instructions and trying there.  All have the exact same behaviour.

---

### Post by JonoBNZ on 2015-12-18
Anyone have any suggestions for any further information I can gather that might help with this?

---

