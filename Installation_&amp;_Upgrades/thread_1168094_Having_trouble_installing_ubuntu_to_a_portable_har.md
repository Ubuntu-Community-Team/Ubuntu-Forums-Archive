---
title: "Having trouble installing ubuntu to a portable harddrive"
date: 2009-05-23
forum: Installation &amp; Upgrades
---

### Post by paulthom12345 on 2009-05-23
Hi,
I recently repartitioned my 250Gb hard drive into three new partition, a main one with about 230GB and two others of about 10GB each. My plan was that i would install live versions of ubuntu, kbuntu and others onto those two partitions. 

Using ubuntu 9.04 i made a live usb with the tool in System -> Administration -> USB Startup Disk Creator. But when i rebooted my computer it didnt load ubuntu up, it just continued over to windows.

Im just looking for a bit of help in how to solve this problem.;)

Cheers
Paul

---

### Post by AndMei on 2009-05-23
Paul

Did you select the USB as a boot option in the BIOS? I haven't used the USB creator in 9.04 yet, so can't comment on its workings yet. I'll be trying it later though.

Cheers

---

### Post by paulthom12345 on 2009-05-23
Wait, found it out, the problem was that USB was first to boot, but Removable storage wasnt, so i changed that and it fixed it all :) YAY

---

