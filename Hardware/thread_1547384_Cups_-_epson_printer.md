---
title: "Cups - epson printer"
date: 2010-08-06
forum: Hardware
---

### Post by pfastre on 2010-08-06
Dear Forum members

I'm using CUPS to get an Epson ALCX21 to work. It works, but I'm trying to set the resolution to 600dpi in color, but with no success.
I tried the following parameters:
  -o Resolution=600dpi -o EPRendering=None => works, monochrome
  -o EPRendering=None => works, prints 600dpi monochrome
  -o Resolution=600dpi => does not work, it prints in color but not in 600dpi (only 300dpi)

Setting the default parameters using the CUPS web interface never works in any way. I can verify this using the monochrome option, which works using the command line but not via the web interface. Maybe if someone knows what I'm doing wrong there, this could help solve the problem too!

I hope someone can help or put me into the right direction! Many thanks in advance!!

Peter Fastré
Belgium

---

### Post by ellgor on 2010-08-07
Hi,

I would recommend going to this site "avasys" and look for the driver for your model, or nearest to it, if it has a scanner as well   if you scroll down on the same page as you download you will see an app called "imagescan" get that as well, after installing needs a reboot to work properly.

Regards, Ellgor.

---

