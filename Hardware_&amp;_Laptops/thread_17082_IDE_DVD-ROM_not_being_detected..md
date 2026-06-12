---
title: "IDE DVD-ROM not being detected."
date: 2005-02-25
forum: Hardware &amp; Laptops
---

### Post by leech on 2005-02-25
I just installed a Toshiba DVD-ROM drive (model number SD-M1912, if I recall correctly).  I tried booting off the live CD and it worked fine.  Then again the Live CD detects my SATA DVD burner ok as well.  It's installed as Master on the first chain, so it should appear as /dev/hda, which it does under the LiveCD, but not in my already installed Hoary.  Anyone know which modules need to be loaded for this?  I've tried 'ide-cd' and I believe the chipset module that it loaded automatically for the IDE was amd74xx.  I also have ide-core and ide-scsi loaded.  I think the ide-scsi is loaded due to the sata drive, not sure though.

This is just a guess, but probably if I re-installed, then it would be properly set up, but of course I don't want to re-install until I get my two new 200gb SATA hard drives (sometime between Monday and Wednesday).  Any ideas how to get this up and working until then?  I know it's set up right, I just watched Sky Captain and the World of Tomorrow on the drive in Windows.  

Leech

---

