---
title: "Hardware error causing boot to hang"
date: 2006-11-01
forum: Hardware &amp; Laptops
---

### Post by Stex on 2006-11-01
On booting ubuntu edgy, before the splash screen appears, everything will stop for ~10 seconds after grub has announced the kernel and shown the word "boot". After this an error message is shown for a split-second before the splash appears and everything boots normally.

> [17179588.184000] PCI: Cannot allocate resource region 0 of device 0000:05:00

As far as I can tell all of my hardware works fine, I can't find any reference to these numbers in things like lspci but I'm quite new to linux so I might be missing things here. I can't find any system/error logs that mention this either.

I've looked around filed bugs about this kind of thing and it seems to have to do with Intel graphics cards, which I have. But I've not seen a report of it slowing down boot times so drastically.

Or is it normal to take time before the splash is loaded? I hope not, would cut a big chunk of my booting time off to get this out of the way.

---

### Post by red_Marvin on 2006-11-01
I get two similar (can't remember if it's "resource region 0" or "upper resource region" or something) errors on an old laptop, but it seems that if I just leave it on it continues to boot after a minute or so...
I have no idea why though...

/*
Just grasping for straws here, but the error sounds like it expect's more hardware to be present. Do you know if the error appears if you plug it into a docking station (which (guessing here) extends the pci bus(?))?
*/

Note that the last paragraph might be way off, and I mean the "my cup holder is broken"-kind of way off...

---

### Post by Stex on 2006-11-01
My laptop doesn't have any kind of dock port that I know of. The only things missing when it boots is removable media, DVD drive, camera cards, usb sticks. Certainly not something it should be expecting to find.

Is a Fujitsu Amilo PI

---

