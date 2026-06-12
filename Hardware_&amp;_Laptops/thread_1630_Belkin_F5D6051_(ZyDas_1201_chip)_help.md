---
title: "Belkin F5D6051 (ZyDas 1201 chip) help?"
date: 2004-10-22
forum: Hardware &amp; Laptops
---

### Post by ewangr on 2004-10-22
I have just installed the 1.0 release of ubuntu onto my machine at home, and am quite pleased at how well it runs on an older box.

However, my network connection needs to be wireless, and the device I have for that is a Belkin F5D6051 USB stick that uses the ZyDas 1201 chip.

Looking at the homepage for the driver for this chip (linux-lc100020.sourceforge.net), it appears that it might be possible to use the latest wlan-ng driver to run this if one can patch the kernel and add the code for the device ({USB_DEVICE(0x50d, 0x6051)}, /* Belkin F5D6051 usb adapter */) to the zd1201.c file.

To say that I'm at a bit of a loss on how to patch the kernel using ubuntu, let alone how to mess with the included drivers, is a bit of an understatement :-) I have rebuilt kernels before, but usually either as a "build from scratch" or following a step-by-step. Patching seems to take things to a whole new level :-)

If there's anyone out there who has already done this for their setup, or who can at least get me started, I'd appreciate it. Since I don't have network access from that machine (Catch-22 anyone?), the more complete you can be - particularly for files I need to DL and copy - the better.

Thanks in advance,
Ewan

---

