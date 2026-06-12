---
title: "Do you have USB 2.0 (high speed) working?"
date: 2007-06-21
forum: Hardware &amp; Laptops
---

### Post by AriciU on 2007-06-21
I'm using 7.04 feisty with the 2.6.20-16 Kernel. It does not recognise any of my USB 2.0 devices even if i connect them on the 2.0 ports.

It sets them back as USB 1.1 (ohci_hcd instead of ehci_hcd) witch means a slow speed of 12mbit.

This is quite frustrating with camera pictures or external hard drives.

So... please install usbview (apt-get install usbview), run it and check out the **USB Version and speed** of your USB devices that you have connected.

Also, please post the kernel version you are using.

Thanks

---

### Post by CrispyFried on 2007-06-21
yes, usb 2.0 works on my notebook, came right up out of the box. I just plugged a flash drive in with usbview runing and it came up under the ehci section with 480 mb xfer rate..

usbview list 1 ehci controller with 6 ports (notebook only has 2 though) and 3 uhci controllers of 2 ports each.

cant seem to copy the text output of usbview or Id post the results.

this is with the 2.6.20-16 generic kernel.

---

