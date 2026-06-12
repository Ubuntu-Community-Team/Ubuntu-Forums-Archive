---
title: "Missing NTFS"
date: 2008-07-10
forum: Hardware
---

### Post by pumakuma on 2008-07-10
I have installed Ubuntu 8.04 on my friends HP Notebook. On his notebook existed a 200gb harddrive belonging to the NTFS partition. After 2 attempts to install from Ubuntu cd from Windows Vista it said "Complete" but then the whole application froze and the Grub never loaded. Then I loaded from the Ubuntu CD and partitioned 10gb of space for Ubuntu. After restarting I have noticed that the Windows Vista installation is no where to be found. It was not found in the Grub at boot and upon typing "sudo fdisk -l" 

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6e236e23

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23565   189285831   83  Linux
/dev/sda2           23566       24321     6072570    5  Extended
/dev/sda5           23566       24321     6072538+  82  Linux swap / Solar


-I was not able to find my NTFS Partition anywhere. How can I get windows to show up in linux and how can i get vista to boot again

---

### Post by Shaythong on 2008-07-10
Maybe it got deleted. :|

---

