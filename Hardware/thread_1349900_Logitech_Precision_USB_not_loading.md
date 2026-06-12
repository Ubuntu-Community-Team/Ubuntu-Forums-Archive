---
title: "Logitech Precision USB not loading"
date: 2009-12-08
forum: Hardware
---

### Post by Rannos.Stoneshield on 2009-12-08
Everything I'm finding on this is eons old (in computer terms) and is not working.

I plug in my USB Logitech Precision controller and nothing happens.  dmesg output does not show it.  I followed a bunch of different guides last night, and I can't tell exactly what modules I loaded with modprobe but I finally got it reporting...once.  jscal and jstest said there was no device found.  I made the /dev/input/js0 etc. entries like I read in a guide and now it says "No such device".

So I rebooted.  I hadn't rebooted with the gamepad plugged in, maybe this would do it.  After all, most people I'm reading have theirs work just by plugging it in.

Well now dmesg doesn't show anything when I unplug/plug the gamepad in and now I can't figure out what module I loaded last night that did let it show up in dmesg, even though it wasn't working and the input devices were not there.


This gamepad works fine on my Mac so I know it's not the gamepad, and that USB port works fine for other devices.

The last time I ran linux with this gamepad  I was using Gentoo and compiled everything by hand and this gamepad worked then...so I'm not sure why it's not coming up, the device entries are not there, etc.


I'm running 9.10 with kernel 2.6.31-16-generic.  I have not recompiled the kernel.

---

