---
title: "HDD cannot be written to, get I/O errors"
date: 2005-12-02
forum: Hardware &amp; Laptops
---

### Post by Dark_Link2135 on 2005-12-02
Aight this HDD worked absolutely in fine, but when I went to install Gentoo linux, I got multiple I/O errors when trying to write a partion table to it, and the same is true when I tried to install Ubuntu.

using GParted gives me this output:

```
Error: Unable to open /dev/hdb - unrecognised disk label.
Warning: Unable to open /dev/hdc read-write (Read-only file system).  /dev/hdc has been opened read-only.
Error: Unable to open /dev/hdc - unrecognised disk label.
Warning: Unable to open /dev/hdd read-write (Read-only file system).  /dev/hdd has been opened read-only.
Error: Unable to open /dev/hdd - unrecognised disk label.
```

I have no idea what it means by a disk label nor how to remedy this problem....anybody able to help me?

edit - i don't have a hdc or a hdd, just sda and hdb.

---

### Post by aysiu on 2005-12-02
Is this a Windows drive?

---

### Post by Dark_Link2135 on 2005-12-03
[QUOTE=aysiu]Is this a Windows drive?[/QUOTE]

It was formerly set up as an NTFS drive, but I never installed Windows on it.  I deleted the partition table anyway, its listed as unpartitioned in gParted.

The only OS I have installed in Ubuntu, the reason I switched was to get away from the BS my college required for Windows boxes connected to the network.  That and I was just fed up with general Windows crap in general :P  I don't want a dual boot, defeats the purpose.

---

### Post by aysiu on 2005-12-03
So what are you trying to do with that hard drive--install Ubuntu onto it? Reformat it as something else for just extra storage space?

---

### Post by Dark_Link2135 on 2005-12-04
[QUOTE=aysiu]So what are you trying to do with that hard drive--install Ubuntu onto it? Reformat it as something else for just extra storage space?[/QUOTE]

Just for extra space, but I got it.  I had the single SATA drive for some reason setup in RAID and this was causing the BIOS not to recognize the HDD.  I rejumpered it as a master so i have /dev/sda and /dev/hda.

---

