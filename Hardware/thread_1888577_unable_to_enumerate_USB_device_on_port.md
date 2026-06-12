---
title: "unable to enumerate USB device on port"
date: 2011-11-29
forum: Hardware
---

### Post by nerderello on 2011-11-29
Hi,
I've read a lot of posts about this error message and ehci_hcd, but there is another reason for it appearing.

I, like many, construct my Linux PC from components, rather than buy them ready made. The motherboard I have at the moment has two sets of USB port, one attached to the motherboard itself and the other set that you can attach (via wires) to the front of the PC's case. It is this second set that I had the problem with.

The motherboard came with a manual (showing, amongst other things which was the positive and negative pins for the second set of USB ports) and the case also came with a manual (actually, it was a scrotty bit of paper) showing which colour wires went to what part of the USB ports on the front of the case.

I followed the manuals (well, manual and scrotty bit of paper) and got these error messages when I tried to plug a USB stick into the front USB ports:

> usb 3-2: device descriptor read/64, error -62
kernel: [   20.080025] usb 3-2: device descriptor read/64, error -62
kernel: [   20.360024] usb 3-2: new low speed USB device number 8 using ohci_hcd
kernel: [   20.768020] usb 3-2: device not accepting address 8, error -62
kernel: [   20.944025] usb 3-2: new low speed USB device number 9 using ohci_hcd
kernel: [   21.352019] usb 3-2: device not accepting address 9, error -62
kernel: [   21.352028] hub 3-0:1.0: unable to enumerate USB device on port 2

What **fixed it** was to switch around the positive and negative wires on the pins (green and white in my case). 

Just thought I'd share this, in case anybody else bumps into it.

---

