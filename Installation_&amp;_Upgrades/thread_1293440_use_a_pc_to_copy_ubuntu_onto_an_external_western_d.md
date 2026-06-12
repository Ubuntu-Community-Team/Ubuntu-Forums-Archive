---
title: "use a pc to copy ubuntu onto an external western digital drive"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by tom373uk on 2009-10-17
My Laptop DVD Rom Drive is not working.I want to be able to install Ubuntu Linux onto an external Western Digital 250GB USB E Book Hard Drive. to use as OS on laptop.
The only way I can see  to do this is by using my PC to copy Ubuntu CD onto the E Book.?
Will there be any problems doing this,and will there be any compatability problem with the Laptop which is an HP Compaq Presario C300 which has the ability to boot from a USB device?:confused:..Any help appreciated [NB I mean a problem such as Windows has when you try to use a copy of the OS generated in another pc!]

---

### Post by hal10000 on 2009-10-17
> The only way I can see to do this is by using my PC to copy Ubuntu CD onto the E Book.?
No, you can not just copy the cd to your harddrive. But you can boot your live-cd from your pc's cdrom drive, plug in your external disk (where you want to install ubunto to)
and install ubuntu into this external drive. There are several threads here regarding this, just search the forum for "ubuntu external harddisk" or something similar, with a little luck you may find a detailed step-by-step procedure.

The main problem is that you can't use the default installation process, you have to take care to install it to the correct drive (your external drive) and that your boot-manager (grub) has to be installed to the mbr of youe external harddisk instead (as per default) to the mbr of your pc's first internal harddisk.

[EDIT]If you succeeded o install it to your external disk, then you have to change the BIOS boot order of your laptop to boot first from your external disk

---

