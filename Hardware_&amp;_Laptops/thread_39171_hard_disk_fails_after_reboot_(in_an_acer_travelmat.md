---
title: "hard disk fails after reboot (in an acer travelmate)"
date: 2005-06-03
forum: Hardware &amp; Laptops
---

### Post by tauko on 2005-06-03
I own an Acer Travelmate 4002WLMi, wich is most-well supported by Ubuntu just after install.

My problem is that one day, without having done anything specific, i restarted and then it stopped working. It happens when it's booting:

* calculating module dependences...
hda: drive not ready for command
hda: drive not ready for command

...

*cannot execute "/sbin/getty"  -> this happens a lot of times

....

buffer I/O error on device hda4, logical block XX


where XX it's from 1, increasing fast. When it says the buffer I/O error then it dies (it doesn't do anything more).

So the, the question is:

- is there any way to try to fix this problem?
- if not, is there any way to backup the data on the hard drive, and then reinstall ubuntu?

let's hope for the first one ^^

PS. sorry for the bad english...

---

### Post by alastair on 2005-06-03
I do not know the problem. But, hardware/disks can fail.

So, it would be worth trying to check the disk by booting something like a "live CD" (e.g. knoppix, Ubuntu) and seeing if you can see the hard disk data.

---

### Post by tauko on 2005-06-04
all the live CD's i've tried doesn't boot, all get stopped....

but booting a DOS, I can see one of the partitons that are in the hard drive (the FAT32 one ^^ )

---

