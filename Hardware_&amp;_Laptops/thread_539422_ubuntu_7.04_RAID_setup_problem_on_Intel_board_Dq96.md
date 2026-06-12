---
title: "ubuntu 7.04 RAID setup problem on Intel board Dq965gf"
date: 2007-08-31
forum: Hardware &amp; Laptops
---

### Post by uscom2 on 2007-08-31
Kindly asking for help

I am trying to install UBUNTU server (7.04) on Intel DQ965GF motherboard.
I have 4 hard dirives 
sda is my system HD, sdb is still empty intended for system backup
they are both SATA and are not insluded in RAID matrix

Then I have another two SATA HD (plugged into SATA 2 and SATA 3 socket) which are set into RAID 1 (mirror) matrix... name of the disk set in BIOS RAID menu is "srw"  on this raid volume I would like to set up a database file....

Problem is that Ubuntu finds another two disks sdc and sdd but not finds the masked disk srw as a representation of these two disks ("linux see thrugh RAID" mask) 

For database purpose I would like to use motherboard hardware RAID instead of Linux softraid (i allready installed EVMS on a system))  for performance purpose... 
disks are 3GBit/s and softraid would not be problem on disk thrughput but on PCI congestion (double write images) 

I kindly ask community to advice how to convince my Ubuntu Linux box to recognise onboard RAID ?
If this is not supported in Ubuntu yet pls advice a workaround..

Thanks in addvance!

Uros

---

### Post by grmmog on 2007-08-31
Is the raid setup handled by the motherboard or by a separate card?  Most motherboard raid setups are actually software raid and not true raid.  The installer can't see the raid because there isn't one.

You can use fakeraid which I believe does support Intel Matrix Storage or linux software raid.  There's plenty of documentation available on the wiki.

---

### Post by Patje on 2007-09-01
May this works. Intel has a cd iamge with drivers for your mobo with debian linux; Give it a try:

[http://downloadcenter.intel.com/confirm.aspx?httpDown=http://downloadmirror.intel.com/11718/a08/INTEL(R)_QSK_VER_2_0_DEBIAN.TAR.GZ&agr=N&ProductID=2372&DwnldId=11718&strOSs=All&OSFullName=All%20Operating%20Systems&lang=eng](http://downloadcenter.intel.com/confirm.aspx?httpDown=http://downloadmirror.intel.com/11718/a08/INTEL(R)_QSK_VER_2_0_DEBIAN.TAR.GZ&agr=N&ProductID=2372&DwnldId=11718&strOSs=All&OSFullName=All%20Operating%20Systems&lang=eng)

patje

---

