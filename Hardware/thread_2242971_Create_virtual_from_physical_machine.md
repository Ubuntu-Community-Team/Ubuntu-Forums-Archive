---
title: "Create virtual from physical machine"
date: 2014-09-05
forum: Hardware
---

### Post by shaikzubair4 on 2014-09-05
I have an PHYSICAL ubuntu OS at 192.168.1.25 that I would like to create a virtualisation of it and access this virtual OS on another machine....Is it possible to acheive this

The map might explain what I intend to do.
[ATTACH=CONFIG]256174[/ATTACH]

---

### Post by fidelis2 on 2014-09-05
With "gnome-disks" (or "dd" in a terminal) you should be able to create a disk image (".img") of your source computer's drive, and then convert this to a virtual disk image to be used with certain Virtual Machine programs.

I know Virtualbox (from the software center) can do such a conversion, see here please:
[http://www.virtualbox.org/manual/ch08.html#idp59139136](http://www.virtualbox.org/manual/ch08.html#idp59139136)

Also, Virtualbox can export its or such a virtual disk image (".vdi") files to other formats. In the main menu "Manager for virtual media" the "copy" button. Export formats are ".vmdk" , ".vhd", ".hdd", ".qed" and ".qcow".

---

### Post by shaikzubair4 on 2014-09-05
thanks I found out..

I used VMWAR vCenter CONVERTER..!!!

---

