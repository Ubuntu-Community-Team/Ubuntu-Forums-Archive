---
title: "Severe problem help pls"
date: 2013-06-21
forum: Hardware
---

### Post by clementchiew on 2013-06-21
ok, i messed up big time. I am a beginner and I have no idea how Linux works. So I have drives A and B, with A partitioned into 1 and 2, and installed Ubuntu into 1. so I decided to format drive B (which had my windows 7) and let 2 be alone (holding Vista). After formatting B, I booted Ubuntu from my cd ( I installed with it) and wiped out 1 (the one holding Ubuntu). I used Gpart. and then, I installed Ubuntu into B(used to be windows 7). After the installation, I cant boot anything at all. I get the black white screen with grub saying "partition not found" and then a command expecting "grub rescue> " I need help seriously, I cant even access my vista now.

---

### Post by 2F4U on 2013-06-21
My guess would be you installed the boot loader grub the second time on B instead of A and the BIOS is set to boot from A. Now, when you deleted the first Ubuntu installation from A this did not delete grub from the MBR of A. When you boot the BIOS looks into the MBR of A and finds the old grub, which points to a partition no longer holding any Ubuntu installation. Therefore, you get the error message that it can't find the partition.
You could try to boot from B (change boot order in BIOS) or fix the old grub or reinstall on B but make sure that grub goes into the MBR of A.

---

