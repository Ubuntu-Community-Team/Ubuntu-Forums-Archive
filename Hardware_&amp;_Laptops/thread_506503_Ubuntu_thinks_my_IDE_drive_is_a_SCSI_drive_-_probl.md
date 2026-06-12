---
title: "Ubuntu thinks my IDE drive is a SCSI drive - problems with VMWare"
date: 2007-07-21
forum: Hardware &amp; Laptops
---

### Post by dwschulze on 2007-07-21
My hardware is a PowerPro A:238 laptop with an IDE drive.  I have a dual boot / VMWare  Feisty / Win XP Pro set up with Win XP running(?) under Feisty in VMWare.  I'm trying to run XP Pro as a native disk in VMWare, which means that it will run the same installation of XP Pro in VMware as when I dual boot.

When I create a vmware virtual machine using the raw disk (sda with Partition 1) vmware warns me that SCSI drives often have problems dual booting and running in a virtual machine.  When I try to start the virtual machine and boot XP Pro GRUB crashes with this message:

    GRUB Loading stage1.5

    GRUB Loading, please wait...
    Error 17


Has anyone else seen this and have a way around this?

Thanks.

---

