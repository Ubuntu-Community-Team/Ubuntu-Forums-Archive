---
title: "gparted warning"
date: 2005-11-18
forum: Hardware &amp; Laptops
---

### Post by Zaare on 2005-11-18
When I run gparted I get the message:
> 
Warning: Unable to open /dev/hdc read-write (Read-only file system).  /dev/hdc has been opened read-only.
Error: Unable to open /dev/hdc - unrecognised disk label.

This seem to result in the fact that I can't resize my drive. I'd appreciate it if someone could tell me what's wrong here?

---

### Post by aysiu on 2005-11-18
What is /dev/hdc?
Can you post the output of ```
sudo fdisk -l
```?

---

### Post by Zaare on 2005-11-19
I'm not sure what /dev/hdc is. The only place I've seen that mensioned is:
[INDENT][http://www.ee.oulu.fi/~iiska/articles/ubuntu_in_a7620.html](http://www.ee.oulu.fi/~iiska/articles/ubuntu_in_a7620.html)[/INDENT]
/dev/hdc is in the kernel boot parameters that are needed for Ubuntu to be able to run on my computer(The details are explained in the page above):
```

hdc=noprobe hdc=cdrom

```

The output of
```

sudo fdisk -l

```
is
> 
Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4676    37559938+  83  Linux
/dev/hda2            4677        4864     1510110    5  Extended
/dev/hda5            4677        4864     1510078+  82  Linux swap / Solaris


---

