---
title: "installing usb scanner"
date: 2007-03-17
forum: Hardware &amp; Laptops
---

### Post by dbbolton on 2007-03-17
i have an HP PSC (printer-scanner-copier) 2175. the printer works perfectly- and all i had to do was plug it in. however, i'm having a bit of trouble getting the scanner to work.
i've installed xsane and sane, but the scanner can't be detected.

first, i ran this :
```
$scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

```

so, i tried 'sane-find-scanner' :
```
$ sane-find-scanner

found USB scanner (vendor=0x03f0, product=0x2b11) at libusb:001:002

```
what's going on ?

---

### Post by scrooge_74 on 2007-03-17
This is not for your scanner, but should point you in the right direction since it is probably driver support what you need.  Read throught the post and you will find the link for driver support.

[http://www.ubuntuforums.org/showthread.php?t=286105&highlight=HP+C3180](http://www.ubuntuforums.org/showthread.php?t=286105&highlight=HP+C3180)

---

