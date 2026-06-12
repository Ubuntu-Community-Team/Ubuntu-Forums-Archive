---
title: "Simple barcode scanner (LC-2013) won't work"
date: 2018-04-21
forum: Hardware
---

### Post by julio-netu on 2018-04-21
I bought a simple barcode reader/scanner, it's imported, so it doesn't have much vendor's information.
It seems to be called LC-2013 
[IMG]https://www.profitstore.gr/images/stories/1-12/prod1/16Spring4/00120.jpg[/IMG]

lsusb:
0483:5750 STMicroelectronics

I seems to work with USBHID by default, when se, if I try to scan a code, it just freezes and I cannot use it again. When I switch to PS/2 mode it properly recognized as a keyboard and won't freeze anymore, but still wont work. 

I would appreciate any help ;)

---

### Post by him610 on 2018-04-22
Here is what shows in synaptic when searching for "barcode scanner".
```

libbarcode-zbar-perl

bar code scanner and decoder (Perl bindings)

ZBar is a library for scanning and decoding bar codes from various sources
such as video streams, image files or raw intensity sensors. It supports
EAN-13/UPC-A, UPC-E, EAN-8, Code 128, Code 39, Interleaved 2 of 5 and QR Code.

This package contains the Perl bindings.

```

I have never tried to setup a barcode scanner, but it may work if you install it.

---

### Post by zerokol on 2018-06-09
Hello @[julio-netu]("https://ubuntuforums.org/member.php?u=2095554"), I got the same problem but when I updated my ubuntu from 16.04 to 18.04, the barcode scanner just started to work. I don't no why, just worked.

---

