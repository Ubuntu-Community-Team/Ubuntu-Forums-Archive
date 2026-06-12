---
title: "USB mouse with svgalib-bin"
date: 2006-05-22
forum: Hardware &amp; Laptops
---

### Post by bpdoyle@gmail.com on 2006-05-22
I have a dell latitude C600 that I just installed a fresh load of ubuntu 5.10.  I am still pretty new to linux, but I am learning.

Most of my hardware has worked fine after the install.  But I have an external USB mouse that I want to use instead of the trackpad.  Gnome detects the USB mouse fine and I can use it no problem in gnome.  But I want to use it to play the quake1 (yes thats quake1 and I recently just started playing it again)

Anyway I downloaded the svgalib-bin package to run quake1.  it tells me I need to specify my mouse in the
/etc/vga/libvga.config

only there is no choice for a USB mouse in the config file.  I tried all of the existing choices to no avail.  So I scrolled further down in the config file and found a place to alternately list my specific mouse device that I want svgalib to use.  it says usually /dev/mouse is a link to your device.  And to specify with:
mdev /dev/ttyS0   #mouse is at /dev/ttyS0

Well I can't figure out what dev my mouse is.  I tried /dev/input/mouse0  all the way up to mouse4 to no avail.  Is there a way to look up the dev (mountpoint?) of my USB mouse.

When I do a 
lsusb
I get the following:
Bus 001 DEvice 002: ID 046d:c016 Logitech, Inc. Optical Mouse

Thanks!

Bryan

---

### Post by dtmilano on 2007-03-26
Use:
```
mdev /dev/input/mice
```

---

