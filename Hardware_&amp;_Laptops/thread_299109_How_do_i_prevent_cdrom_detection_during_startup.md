---
title: "How do i prevent cdrom detection during startup?"
date: 2006-11-13
forum: Hardware &amp; Laptops
---

### Post by altaaa on 2006-11-13
Hello everyone,

Can I make ubuntu edgy not detect my cd rom drive?

I can't disable it in the BIOS (HP NX6110). It appears as /dev/hdb.
I tried disabling it in /etc/fstab; but that didn't work. I googled for this but found no usable info. 

One way of managing this is to completely physically remove the drive, but then I can't use it in Windows. There must be a way... (preferrably without a kernel recompile :))

Edit:
I added 'rmmod cdrom' and 'rmmod ide_cd' to /etc/rc.local. Now both modules are gone from my lsmod output. The drive is absent in gnome.

---

