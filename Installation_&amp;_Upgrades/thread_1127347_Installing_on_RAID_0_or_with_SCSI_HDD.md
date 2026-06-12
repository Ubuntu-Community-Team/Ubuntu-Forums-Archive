---
title: "Installing on RAID 0 or with SCSI HDD"
date: 2009-04-16
forum: Installation &amp; Upgrades
---

### Post by IluvatarMIlan on 2009-04-16
Hello people,

I'm relatively new to Linux and am now trying to install Ubuntu 8.10 on an HP XW9300 Workstation.

This PC has 2x SATA HDD 160GB which I configured in the BIOS as RAID 0. The RAID BIOS lists the array as healthy and it has also worked in the past with a WinXP install, albeit in a RAID 1. (I already deleted the disks and rebuild the array as RAID 0)

The RAID controller is from NVIDIA.

Another HDD I have in the unit is an old SCSI HDD (Seagate 10K, 36GB) which is correctly recognised by the LSI BIOS as well as listed in the regular BIOS under Controllers. 

The problem is that when I enter the Install CD from Ubuntu to install the OS it doesn't recognise the 2 SATA HDD's as 1 logical volume but simply lists 2x 160GB HDD.
Also, the SCSI HDD is nowhere to be found and I can't select it to install the OS on.


I must add that I had exactly the same issues with an OpenSuse install, this one also recognised neither setup correctly, so it doesn't seem to be Ubuntu specific.

Any help on installing Ubuntu on either the RAID 0 or SCSI setup would be greatly appreciated!

Let me know if you need more info.
T.I.A

Milan

---

### Post by Daisuke_Aramaki on 2009-04-16
Have you read these documents first?

Scroll down to look up on RAID documentation

[https://help.ubuntu.com/community/Installation]("https://help.ubuntu.com/community/Installation")

Also this thread might help

[http://ubuntuforums.org/showthread.php?t=408461]("http://ubuntuforums.org/showthread.php?t=408461")

---

### Post by ronparent on 2009-04-16
The following link addresses your situation. It will lead you through the steps to install Ubuntu on raid.

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

As you have already found out, the standard desktop install cd will not let you see a raid array to partition or install to. You will need the 'alternate cd' to ultimately get your system installed. That might also solve your problem finding your scci disk?

---

### Post by IluvatarMIlan on 2009-04-16
Thanks a lot!

All those documents are very insightful.
If I understand it correctly the unit i'm working on doesn't have real HW-based RAID but rather BIOS/FAKE RAID. I checked the following document: [http://h18000.www1.hp.com/products/quickspecs/12186_div/12186_div.HTML](http://h18000.www1.hp.com/products/quickspecs/12186_div/12186_div.HTML) and the remarks about Linux  whenever RAID is mentioned seem to imply this.

I'll definitely check out the alternate CD or might just opt for the SW RAID.
Hopefully I'll get the SCSI running as well...

Thanks people.

---

