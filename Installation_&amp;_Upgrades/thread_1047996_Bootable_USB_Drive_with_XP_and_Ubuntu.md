---
title: "Bootable USB Drive with XP and Ubuntu"
date: 2009-01-23
forum: Installation &amp; Upgrades
---

### Post by cantdrive55 on 2009-01-23
I'm trying to create a usb drive that will contain both the XP and Ubuntu installers. I have 2 separate flash drives now that let me boot off of and install from for each OS but I want to consolidate them onto a single 4GB drive. Any recommendations on how I could do this?

---

### Post by lykwydchykyn on 2009-01-23
The ubuntu part is trivial.  Something like unetbootin will whip that up real quick for you.

The XP part is tricky, you'll want to read up a bit on syslinux and how to configure it.  I don't know if it can chain boot a windows iso or not. 

I tried to make the XP install disc available via pxelinux, but it was just a mess of a setup that never did work.  It's boot structure is much different from Linux booting, so things don't exactly translate.  

check out this mailing list post:

[http://syslinux.zytor.com/archives/2002-October/001135.html](http://syslinux.zytor.com/archives/2002-October/001135.html)

---

