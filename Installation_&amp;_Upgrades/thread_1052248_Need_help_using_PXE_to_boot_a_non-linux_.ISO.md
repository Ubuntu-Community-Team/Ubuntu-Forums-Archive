---
title: "Need help using PXE to boot a non-linux .ISO"
date: 2009-01-27
forum: Installation &amp; Upgrades
---

### Post by digitalbenji on 2009-01-27
Hello,
    I have a functional PXE server set up (built on Ubuntu 8.04.1 Server).  It's running DHCP and working well.  I can easily boot into a LiveCD environment for anything linux based.  This seems to boil down to having the following in my pxelinux.cfg/default file:
```

Label Somelinux
kernel mounted_iso/linux
append init=/etc/init

```

However, I've been unable to get this to boot any generic bootable ISO that I throw at it.  I've tried using ISOLinux, Syslinux, and Memdisk, but am having a really hard time getting this working properly.  I've researched it, and feel like I'm extremely close.  I know this can be done.  Can someone please explain to me exactly how to use the PXE environment to boot from ANY ISO image.  At this point, efficiency is a secondary concern (isolinux -> memdisk -> isolinux, whatever).  I just want to get this working.  I have 80 workstations to image with Ghost (no Ghostcast server available), and being able to put my Ghosted .ISO image onto my PXE server will save me a lot of time and money.

Thanks in advance!

---

### Post by digitalbenji on 2009-02-11
bump

---

### Post by Pumalite on 2009-02-11
Take a look at this. It might help:
[http://images.google.com/images?hl=en&q=PXE+environment+to+boot+from+ANY+ISO+image&um=1&ie=UTF-8&ei=vDGTSYXfNtPGtgeVtpzTCw&sa=X&oi=image_result_group&resnum=1&ct=title](http://images.google.com/images?hl=en&q=PXE+environment+to+boot+from+ANY+ISO+image&um=1&ie=UTF-8&ei=vDGTSYXfNtPGtgeVtpzTCw&sa=X&oi=image_result_group&resnum=1&ct=title)

---

### Post by digitalbenji on 2009-02-11
Thanks, but I'm looking for something a big more concrete than that.

---

### Post by digitalbenji on 2009-03-02
bump

---

### Post by lykwydchykyn on 2009-03-02
I've looked into this as well and unfortunately there doesn't seem to be an easy answer.  If the .iso is small enough you can change the extension to something like ".img" and use memdisk to load it, but it probably won't work for your bootable ghost images.  There is currently no solution I'm aware of to just generically boot ISO's.

I switched from Ghost to g4l a few years ago; it doesn't have all the same features, but it works well for my purposes and is easy to set up as PXE boot.  Just something you might want to look at.

---

