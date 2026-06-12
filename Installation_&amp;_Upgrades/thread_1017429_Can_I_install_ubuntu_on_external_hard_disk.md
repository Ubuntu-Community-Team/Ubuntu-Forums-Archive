---
title: "Can I install ubuntu on external hard disk ?"
date: 2008-12-21
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2008-12-21
A. If I have an external hard disk plug into my pc, can I run any program on it like MySql db, Netbeans, eclispe ? is it seen by the computer as the internal hard disk ?, because if that is the case my second question is probably irrelevant.
B.Is it posible to install ubuntu on external hard disk ?
if so how ?
Thanks

---

### Post by infamous-online on 2008-12-21
Installing ubuntu onto an external is very possible, however installing a program such as mysql, apache and others, no!

Make sure you unplug your main harddrive first and then try to see if the external hd is recognized. Once it has been then you should be able to install on it just fine. However, make your bios can see it first before attempting to try this.

---

### Post by peroyhav on 2009-05-20
I have an external harddrive with Ubuntu and Apache, Mysql and multiple other non standard programs, to be able to boot the intallation i needed to install extlinux because grub didnt recognice the disk after I had unplugged it(think it has something to do with the way grub recognices disks) this will also make the disk bootable on other computers without the need to change the bootconfiguration. make shure that you install grub to the disk you are installing on though. (I needed to reinstall the bootsector on my vista partition because of failing to do this). I have not yet found out how i can make the installation to load drivers and firmware corect for the computer I boot, the only computer fully supported now is the computer I installed on.

---

