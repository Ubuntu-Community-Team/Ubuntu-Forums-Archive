---
title: "SCSI drive not seen on install"
date: 2006-08-14
forum: Hardware &amp; Laptops
---

### Post by bartmanbsd on 2006-08-14
Hello all,

I have an Adaptec 39320A-R U320 SCSI card with a 73 GB U320 hard drive attached to it and when I try and install Ubuntu 6.06 or 6.06.1 it will not recognize the drive.  I am curtly dual booting XP and redhat enterprise 3 with the 2.4 kernel and everything works fine.  From looking around it seems like there has been some issues with the aic7xxx driver on the 2.6 kernel.  

Does anyone have a solution to this problem?  

Would buying a new SCSI card help?  If so a recommendation would be appreciated.

---

### Post by zxee on 2006-08-14
This bug [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/41061](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/41061) seems to be the issue.
You could check out the hardware compatibility database at linuxquestions: [http://www.linuxquestions.org/hcl/index.php/cat/201](http://www.linuxquestions.org/hcl/index.php/cat/201) for scsi controllers that don't use that driver.

---

### Post by bartmanbsd on 2006-08-15
Thanks!  I read that article, but I wanted to make sure that was my problem before I went out and purchased a new SCSI card.  I was thinking about buying the LSIU320 which uses the mtp driver.  Are there any known issues with this driver or card?  Thank you for your help…

Cheers,

JD

---

### Post by zxee on 2006-08-15
I have no personal experiance with that card. It does appear on LQ's HCL
[http://www.linuxquestions.org/hcl/showproduct.php?product=2131&cat=298](http://www.linuxquestions.org/hcl/showproduct.php?product=2131&cat=298) and they say it's supported.
I've uesd adaptec scsi cards in the past but now my drives are ide or sata.

---

