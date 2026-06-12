---
title: "RAID and my sata cd drive"
date: 2010-03-07
forum: Hardware
---

### Post by trorion on 2010-03-07
I'm using raid 0 on a gigabyte ga-ma785gmt motherboard and ubuntu 9.10.  The system installed fine and is running but the SATA CD drive isn't recognized in SATA mode (it hangs on the bootup and eventually the bootlog gives up on the drive).  When I instruct the bios to use SATA 5 as an IDE drive the CD works fine (the CD is installed on sata hub 5)

the manufacturer disks do seem to have a linux option but I'm not sure what to do with it and the manual is worthless for this.
/media/cdrom0/boot/isolinux
	isolinux.bin
	isolinux.cfg
	txtmsg

I'm fairly confident that the the AHCI drivers are the problem.  any suggestions?  And I guess..does it matter?  I'm not sure that a DVD running on ide is any slower than the same dvd running on sata.

---

