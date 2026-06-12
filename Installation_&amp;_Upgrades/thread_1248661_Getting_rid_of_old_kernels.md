---
title: "Getting rid of old kernels"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by frankwakeman on 2009-08-24
When I boot up my laptop I've now got I think four kernels to pick from and I've never known how to delete these or whether they're just grub entries.  The latest seems fine so how would I get rid of all but the one ending ...15?

Thanks in advance.

---

### Post by raymondh on 2009-08-24
You can edit (comment) the /boot/grub/menu.lst or, open synaptic and search for/install startupmanager.  SUM is GUI-based which also writes to the menu.lst.  In SUM, you can set defaults, kernels to show, time to boot, etc.

Post back if you want to try manually editing the menu.lst.  It involves your gedit (or favorite editor) and putting a # (comment) in front of the kernels you don't wish GRUB to read.

---

### Post by Operan on 2009-08-24
You can remove old kernel by typing this command to terminal:
> sudo apt-get remove linux-image-2.6.28-xx-generic
xx: Your old kernel, ex: 11,13,...

---

### Post by nico_forgot on 2009-08-27
i find that looking up older kernels in the grub menu and getting rid of them with

```
$ sudo aptitude purge linux-image-2.6.2x-xx-generic
```

is more efficient. it removes the kernel image and dependent, now obsolete, files, too. i also usually run

```
deborphan
```

after major file install/removal. maybe that's a personal thing.

synaptic also make it easy in a gui. search for installed packaged with the filter 2.6.2 and mark older images for complete removal.

works for me anyway. i'd take it with a grain of salt. cheers -

---

