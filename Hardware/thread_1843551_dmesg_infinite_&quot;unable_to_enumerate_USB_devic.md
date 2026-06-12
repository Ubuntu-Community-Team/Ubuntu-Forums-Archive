---
title: "dmesg infinite &quot;unable to enumerate USB device&quot;"
date: 2011-09-13
forum: Hardware
---

### Post by N00b-un-2 on 2011-09-13
here is a sample of what I see at boot and when using the terminal

```
[ 1382.756107] hub 2-0:1.0: unable to enumerate USB device on port 5
[ 1383.008104] hub 2-0:1.0: unable to enumerate USB device on port 5
[ 1383.260100] hub 2-0:1.0: unable to enumerate USB device on port 5
[ 1383.512122] hub 2-0:1.0: unable to enumerate USB device on port 5
[ 1383.764118] hub 2-0:1.0: unable to enumerate USB device on port 5
[ 1384.016092] hub 2-0:1.0: unable to enumerate USB device on port 5

```

That is what happens when I run dmesg.  I get this error constantly at boot and often when I'm doing other things in the terminal.
I have noticed this problem on the same laptop for a while now.  This issue is not specific to Ubuntu, but rather with the kernel itself.  I get the same error on Ubuntu, Mint, Debian, OpenSuse and Fedora.  To the best of my recollection, the issue first began with kernel 2.6.29, but I'm inclined to believe it's not a kernel error but rather an indication of the hardware itself failing and the updated kernels are just making me aware of the problem.  Just for troubleshooting purposes I've downgraded back to 8.04 and the dmesg errors have indeed gone away, but the intermittent usb connectivity has not and my wifi signal is regularly between 20-40% despite being only a few feet from the router.  In the last several weeks my computer (an HP DV2000 laptop) has been suffering from drastically decreased performance, frequent crashes and of course the never ending dmesg error.

If I had to guess, I would say that it sounds like the USB controller among other things on the motherboard itself is failing and has been for quite a while.  I get errors often when plugging in usb devices on Windows saying that the device is plugged into a USB 1.1 port when my laptop has none.  On linux as well as Windows, devices often randomly disconnect and reconnect.

I'm thinking its just time for a new laptop but wanted some feedback before I throw the baby out with the bathwater.

---

