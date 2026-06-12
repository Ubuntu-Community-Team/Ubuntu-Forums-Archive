---
title: "Print Quality Issues (Generic Foomatic drivers)"
date: 2010-12-06
forum: Hardware
---

### Post by mcgodx on 2010-12-06
Hey all,

I am using Ubuntu 10.10 at work and it's working out great for the most part, and with most tasks I am more productive now than I was with Windows.

There's one problem that I have, however...

The printer we use at work is a Ricoh 2232C which is unsupported using the native driver (I have tried the version found in CUPS by default, and it just prints out postscript code).  The same behavior occurs when I rip the file out of a Windows driver package.

I have found that the driver "Generic Printer - Foomatic/hpijs-pcl5c [en]" gets the job done, although at 300 DPI (the printer is capable of 600), and colors are blurry and not particularly accurate.  Duplex works, though which is a big issue for what we print out.  I tried messing with the quality/dpi settings and noticed 0 change.

The driver "Generic Printer Foomatic/cljet5 [en]" seems to give better results, although it claims only ~4K colors they look more vibrant and although it also says only 300 DPI everything is much more sharp.  The big problem here is a lack of duplex support.

Is it possible to somehow add duplex support to the "Generic Printer Foomatic/cljet5 [en]" driver?  Or maybe change some information in the other driver to match that of the cljet5 driver?

Thanks.  Hope I posted this in the right forum.

---

