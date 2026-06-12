---
title: "no more USB on my Thinkpad!!"
date: 2005-12-13
forum: Hardware &amp; Laptops
---

### Post by greenway on 2005-12-13
Hi guys, would really appreciate some help on this; it seems like the whole USB system is out. There are no special drive types showing in /dev and nothing happens when I plug any kind of USB device into the bus. However, my USB busses do show up in System/Administration/Device Manager.

I really need this get this working again kinda quick since I am not able to use my Thinkpad (using an old 600x) to get on the internet.

Thanks much!

---

### Post by greenway on 2005-12-13
Problem fixed by adding the "acpi=off" option to the kernel line in menu.lst. This is just something I found in another thread and I still have no idea why this parameter is required all of a sudden.

Anybody with some hardware knowledge out there who could give me some more insight on this issue? tnx!

---

### Post by greenway on 2005-12-13
Well, the "acpi=off" thingy is also not working out very well. Now I am unable to mount my cdrom! It doesn't automount after putting a CD in and there's no cdrom listed in /dev!!!

Anybody??!! I would like to be able to use both my cdrom and my USB devices!

---

