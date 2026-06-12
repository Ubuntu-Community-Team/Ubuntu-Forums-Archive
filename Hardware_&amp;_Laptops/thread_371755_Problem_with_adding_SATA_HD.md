---
title: "Problem with adding SATA HD"
date: 2007-02-27
forum: Hardware &amp; Laptops
---

### Post by Demoncrat on 2007-02-27
Hello,


I have the following problem with Ubuntu Edgy atm.

I have one harddrive installed atm (SATA 300GB), which looks like this:

fdisk -l /dev/sda

Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3916    31455238+  83  Linux
/dev/sda2            3917       36483   261594427+   f  W95 Ext'd (LBA)
/dev/sda5            3917        3929      104391   83  Linux
/dev/sda6            3930        6361    19535008+  83  Linux
/dev/sda7            6362        7577     9767488+  83  Linux
/dev/sda8            7578        7670      746991   82  Linux swap / Solaris
/dev/sda9            7671       36483   231440391   83  Linux
/dev/sda10           3930        3930           0+  83  Linux
/dev/sda11           3930        3930           0+  83  Linux

Partition table entries are not in disk order


I also have a second disc (SATA 200GB) which started to act weird lately, so i wanted to add a 3d HD, to do a rescue of the 200GB disc. However, when i connect this 3rd HD (recognised by the bios), Ubuntu will no longer boot in normal mode (it just sits at the splash screen and doesn't move). When I tried to boot up in recovery mode, i got an error message after a few minutes, which said that it could not mount the root file system on /dev/sda6 (my root partition). When I remove the 3rd HD again, everything works fine again.

Anyone who has an idea what might be wrong ?

---

### Post by Demoncrat on 2007-02-27
I've solved the problem myself, but I'd like to share the solution with you, in case someone ever comes across the same problem.

The motherboard is ASUS A8N-E (Nforce4 chipset).

My 1st HD (with my system files) was connected to the MB on SATA1 recognised by Ubuntu as sda, the 2nd HD (data disk) was connected on SATA2, recognised as sdb. When I added the 3rd HD (which i connected on SATA3), the order in Ubuntu changed suddenly. The HD on SATA1 was recognised as sdb, the HD on SATA2 became sdc and the HD on SATA3 became sda. So I switched the 2 HD's on the MB (being 1 and 3), went into the BIOS and told the system to boot from SATA3. This solved the problem. I don't know if this is an Ubuntu problem or an nForce4 problem atm, if anyone can enlighten me about this behaviour, please do so.

---

### Post by RobotJox on 2007-03-05
thank you SO much for posting this solution.

I have the exact same mobo and were experiencing the same problems after adding 2 new sata drives.

Your post saved me hours of work - thanks!!! I love this forum!!!

---

### Post by mreynolds on 2008-01-26
Thanks a million for coming back and posting the solution. I've been trying to get this to work on my MSI K8N Diamond Plus.

I swapped cables around, messed with the drive order in the bios, nothing. I think I kept mismatching the drives and their order.

Anyway, thanks :)

---

