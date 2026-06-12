---
title: "udev, sata, vmware guest"
date: 2006-05-29
forum: Hardware &amp; Laptops
---

### Post by Eman_Resu on 2006-05-29
I am dual booting WinXP and Ubuntu.  I have a laptop with a SATA drive.  When booting Linux, the drive is labeled as a SCSI disk ( /dev/sda1 ).  When using VMWare, the drive is labled as IDE ( /dev/hda1 ).  Is it possible to create a udev rule to rename the IDE labled drive to a SCSI labled drive?

---

### Post by Sutekh on 2006-05-29
[quote=Eman_Resu]I am dual booting WinXP and Ubuntu.  I have a laptop with a SATA drive.  When booting Linux, the drive is labeled as a SCSI disk ( /dev/sda1 ).  When using VMWare, the drive is labled as IDE ( /dev/hda1 ).  Is it possible to create a udev rule to rename the IDE labled drive to a SCSI labled drive?[/quote] Sure can.  

I have a HOWTO for writing udev rules, I hope it can help.  If not I'm sure I can.

[Ubuntu Forums - Create your own udev rules to control removable devices]("http://www.ubuntuforums.org/showthread.php?t=168221")

---

