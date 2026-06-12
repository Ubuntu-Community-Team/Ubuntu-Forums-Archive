---
title: "Possible SSD Failure"
date: 2014-02-18
forum: Hardware
---

### Post by bookrt on 2014-02-18
I am running LUbuntu 12.04 LTS on an OCZ SSD about 1 yr old. Started having problems with XBMC black screen last night. Now on boot the desktop loads properly but the wireless mouse does not work and Wifi does not connect. I am thinking there may be some bad sectors. I boot using USB stick and run disk utility. SMART self-test stalls out after about 10 seconds and does not report any results. In the box with various data, I see the following:

198 Uncorrectable Error Count Normalized=173 Worst=150 Threshold=0 Value=23051
199 UDMA Normalized=138 Worst=112 Threshold=0 Value=12845

Would the "value" number be referring to the actual SSD test result, and would these be worrisome numbers?

Would this indicate total failure, or would you advise to attempt reinstallation?

Thanks!

---

### Post by bookrt on 2014-02-18
PS fsck /dev/sdb1 reports the file system is clean. Same with "Check File System" in the Disk Utility GUI.

---

### Post by bookrt on 2014-02-19
Updating...So far reinstall has gone smoothly (after fixing UEFI options in BIOS, arghhh). Still I would appreciate feedback on the SSD SMART data. Should I be concerned about disk health?

---

