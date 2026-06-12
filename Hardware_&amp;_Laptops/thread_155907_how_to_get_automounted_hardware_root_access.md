---
title: "how to get automounted hardware root access?"
date: 2006-04-06
forum: Hardware &amp; Laptops
---

### Post by jnev on 2006-04-06
what do I need to add to my fstab so that all of my hardware (flash drives, memory cards, external hard drives, etc) that I connect to my computer gets root access without me having to open with 'sudo nautilus'?

thanks

---

### Post by aysiu on 2006-04-06
That should already happen.

This may help, though:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

It'll most likely be /dev/sda1 instead of /dev/hda1 and FAT32 instead of NTFS.

---

