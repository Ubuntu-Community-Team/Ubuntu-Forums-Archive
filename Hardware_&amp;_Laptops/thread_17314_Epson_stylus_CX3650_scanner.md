---
title: "Epson stylus CX3650 scanner"
date: 2005-02-27
forum: Hardware &amp; Laptops
---

### Post by thump on 2005-02-27
Hi.
I'm a new Ubuntu user and I'm having a little trouble with my new printer. It's an Epson stylus CX3650. I finally got the printer working by installing gimpprint drivers and selecting CX3200, but I don't know how to install the scanner, and when I start xsane it tries to scan from my tv card. How do I get my tv card out of there? and how can I add my scanner??
when I do:
```
sane-find-scanner
```
I get:
```
found USB scanner (vendor=0x04b8, product=0x080e) at libusb:001:004
```

---

### Post by kxs on 2005-06-27
I managed to use CX3650 `s scanner with XSane by doing this:
> This is a multifunction device I got to work using Gimp-print's CX3100 driver.
I tried it with 100x100, 360x360, 720x360 (no apparent difference from 360x360)
and 720x720; other resolutions I didn't try, nor did I try photographic paper,
etc.

The scanner works too, and it is identified by SANE as a CX3600, but only after
doing this:

1) Get the manufacturer & product numbers:

# sane-find-scanner
[...]
found USB scanner (vendor=0x04b8 [EPSON], product=0x080e [USB MFP]) at
libusb:001:002
[...]

2) Modify /etc/sane.d/epson.conf to look for it by adding these numbers to the
"usb" line:

usb 0x4b8 0x80e

3) Add a line for this scanner to /etc/hotplug/usb/libsane.usermap:

# Epson Corp.|Stylus CX3600
libusbscanner 0x0003 0x04b8 0x080e 0x0000 0x0000 0x00 0x00 0x00 0x00 0x00 0x00
0x00000000

4) Turn multifunction off, restart the hotplug subsystem and turn multifunction
on

5) Add users who want to scan to the "scanner" group

6) Ready!
original text is here:
[HTML]http://www.linuxprinting.org/pipermail/epson-list/2004q4/004125.html[/HTML]

To be honest I`m not sure about 4). What to do exactly? Turn multifunction off? Is it some option or the printer itself?
Anyway, it works for me  :)

---

