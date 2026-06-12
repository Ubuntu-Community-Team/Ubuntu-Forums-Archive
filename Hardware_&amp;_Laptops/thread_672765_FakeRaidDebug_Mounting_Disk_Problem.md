---
title: "FakeRaidDebug: Mounting Disk Problem"
date: 2008-01-19
forum: Hardware &amp; Laptops
---

### Post by eigenVector on 2008-01-19
I'm getting the 'No Raid Disks' error in dmraid trying to mount two 250Gb disks that were raided with my ULi m5288 Controller when in windows.  
I've been going through the FakeRaidDebug and ran the dd command and attached the  output file since dmraid -rD didn't generate any files.

output from dmraid -b:
/dev/sda:    488397168 total, "WD-WCANKC538461"
/dev/sdb:    488397168 total, "WD-WCANKC533859"


output from fdisk -u -l /dev/sda:
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x31cd466f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   976784129   488392033+   7  HPFS/NTFS


any ideas what I should do next?

---

