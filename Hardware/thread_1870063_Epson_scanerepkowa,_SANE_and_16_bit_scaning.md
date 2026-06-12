---
title: "Epson scaner/epkowa, SANE and 16 bit scaning"
date: 2011-10-26
forum: Hardware
---

### Post by michalus on 2011-10-26
I am using Epson v500 scaner with epkowa driver. 

iscan 2.27.1-4
iscan-data 1.11.0-1
iscan-plugin-gt-x770 2.1.1-1                                    

Driver is working. I am able to scan with XSane/Sane, iscan or Vuescan. 

Vuescan scans images with 16 bit depth. But whenever I choose 16 bit depth on "epkowa config panel" in XSane program is crashing.

I've found some old posts at:
[http://lists.alioth.debian.org/pipermail/sane-devel/2008-June/022224.html](http://lists.alioth.debian.org/pipermail/sane-devel/2008-June/022224.html)
which describing some problems with 16 bit depth on some Epson scaner. 

Can somebody confirm that it still doesn't work? Or maybe somebody using it without problems. I need feedback. 

I'd like to use Negfix script:
[https://sites.google.com/site/negfix/](https://sites.google.com/site/negfix/)
so I don't need most features of Vuescan and its Pro license (for "raw scaning").

---

### Post by martinbarlow on 2012-12-01
I have exactly the same issue with epson perfection v30

ubuntu 12.10

iscan                                     2.29.1-5~usb0.1.ltdl7
iscan-data                                1.18.0-1
esci-interpreter-gt-f720                  0.1.1-2

libksane-data         4:4.9.2-0ubuntu1
libksane0         4:4.9.2-0ubuntu1
libsane:i386         1.0.23-0ubuntu1
libsane-common         1.0.23-0ubuntu1
libsane-hpaio         3.12.6-3ubuntu4
sane-utils         1.0.23-0ubuntu1
xsane         0.998-3ubuntu3
xsane-common         0.998-3ubuntu3

---

