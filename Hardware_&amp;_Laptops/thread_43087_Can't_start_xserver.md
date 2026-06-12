---
title: "Can't start xserver"
date: 2005-06-20
forum: Hardware &amp; Laptops
---

### Post by ShaneR on 2005-06-20
Hello, all.

I've just installed ubuntu this afternoon.  Everything went well, but I can't start xserver.  Here's the info:

1) Older HP Celeron 633 Mhz, 512 MB ram.

2) The motherboard has onboard video (i810), but  a couple of years ago I put in a Gforce4 mx420 PCI card.

3) no option to disable onboard video in bios (only option for primary boot [onboard or PCI])

4) I manually configured xserver to use the "nv" driver, with default PCI bus location.

5) looking at error log, it states that no device exists at 1:8:0.  However, this IS the correct bus location for the card.

6) Had this card working fine under SuSe.

Any help would be appreciated!

Thanks :)

---

### Post by guX on 2005-06-21
The xserver wouldn't start for me when I first installed Ubuntu. I set the driver to "vesa", and then I could start the xserver.

---

### Post by ShaneR on 2005-06-21
I tried Vesa as well with no luck.  It returned another error message (that I can't remember).

I'm wondering if I manually download and install the Nvidia drivers  would cure it.

Thanks :)

---

### Post by ShaneR on 2005-06-21
Got it working :)

I had to manually edit  xorg.conf through nano  to the proper bus location and disable the frame buffer.

All is good...

Thanks!

---

