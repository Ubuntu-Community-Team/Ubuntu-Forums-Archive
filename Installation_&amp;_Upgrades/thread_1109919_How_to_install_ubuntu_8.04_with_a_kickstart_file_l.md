---
title: "How to install ubuntu 8.04 with a kickstart file located on a floppy ?"
date: 2009-03-29
forum: Installation &amp; Upgrades
---

### Post by FredDT on 2009-03-29
Hi:

I want to set up an automated installation of ubuntu 8.04 server using a kickstart file located on a floppy drive while booting on the installation CDROM.
I've remastered the CDROM with the following isolinux.cfg:

```
DEFAULT install
LABEL install
  kernel /install/vmlinuz
  append  ks=floppy:/ks.cfg  initrd=/install/initrd.gz  --
```

It looks like Ubuntu is unable to mount the floppy.


Any suggestions ?

---

