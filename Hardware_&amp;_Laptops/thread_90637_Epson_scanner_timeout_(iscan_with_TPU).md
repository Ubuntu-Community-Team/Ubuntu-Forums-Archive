---
title: "Epson scanner timeout (iscan with TPU)"
date: 2005-11-15
forum: Hardware &amp; Laptops
---

### Post by abuegel on 2005-11-15
Hello out there,

I am using my Epson Perfection 1650 Photo with Epkowa's iscan for a long time with Mandrake. After installing Ubuntu Hoary, I had no chance to get highres scans to work with the TPU. There is a timeout issue. Mandrake made no such problems to me! Now with Breezy it's the same: no highres scans (tried 1200/1600 dpi) with the TPU. XSane works perfectly in all resolutions, iscan does it only with lowres scans (without TPU). Timeout is somewhere at 40 seconds, but my Epson needs somewhat more than that with the TPU attached.

Do I have the possibility to change the timeout somewhere? Is it the usb subsystem in Ubuntu? Is it the kernel (Mandrake 2.4 <-> Ubuntu 2.6)? Is it hotplug? The one thing I don't understand is, that XSane works fine in all resolutions and iscan only works with low resolutions. But for me XSane is no alternative. iscan is way better.

Can someone give me a hint?

Thanks for your help in advance and sorry for my bad english #:-|

Andreas :)

---

### Post by kosmic on 2005-11-15
hum i've never used iscan, but you should look in the iscan configuration file, to see if you can change the parameters

---

### Post by abuegel on 2005-11-16
Solved the problem! I had to build from source and put a bigger timeout (originally 30 seconds) in the sanei/sanei_usb.c:

--- snip ---

#ifdef HAVE_LIBUSB
static int libusb_timeout = 60 * 1000;  /* 60 seconds */
#endif /* HAVE_LIBUSB */

--- /snip ---

Maybe this will help anyone with the same thing. I wonder if noone but me had that issue. Perhaps I should tell Epkowa about that...
Thanks for reading and replying!

FYI: the timeout value is coded into libsane-epkowa.so (/usr/lib/sane)

Andreas :-)

---

