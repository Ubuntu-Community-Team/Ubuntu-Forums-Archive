---
title: "No SMART Data &amp; Self Test Options For SAS Drives In Disks Utility"
date: 2015-09-06
forum: Hardware
---

### Post by ste6e on 2015-09-06
Hello All,  

My 'SMART Data & Self Test' is grayed out in the 'Disks' utility for HBA SAS drives.  I can use  'SMART Data & Self Test' in the 'Disks' utility for motherboard SATA drives.   As a further confusion, I can use terminal & GSmartControl to see the HBA SAS Drives, but I cannot in the 'Disks' utility.   ...I would prefer to run SMART test & check SMART data thru the standard 'Disks' utility.   Am I missing some setting?  

As further background, I have a Lenovo TS440, running Ubuntu Desktop 15.04, using an IBM 1015 with P19 version of 2118IT firmware (IT Firmware) as the HBA to SAS drives.  I can read, write, & format the HBA SAS drive thru 'Disks' utility, but curiously 'Disks' doesn't seem to support SMART Tests or Data of my HBA SAS drives.

Best Regards,
     Steve :(

---

### Post by tgalati4 on 2015-09-06
Welcome to the forums.  Smartmontools (*smartctl*) has limited RAID support. If your card is not listed, then you won't get SMART data from those disks:

[https://www.smartmontools.org/wiki/Supported_RAID-Controllers](https://www.smartmontools.org/wiki/Supported_RAID-Controllers)

Post the output of a drive:

```
sudo smartctl -i /dev/sdj
```

---

