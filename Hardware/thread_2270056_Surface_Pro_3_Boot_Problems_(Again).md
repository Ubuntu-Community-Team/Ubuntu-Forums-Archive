---
title: "Surface Pro 3 Boot Problems (Again)"
date: 2015-03-19
forum: Hardware
---

### Post by canadian05 on 2015-03-19
I started out trying to dual boot Ubuntu 12.04 and 14.10 separately, while neither would work for very long. It seemed that booting into Windows broke my ability to boot into Ubuntu. After a lot of frustration trying to fix it with boot repair I gave up and installed only Ubuntu 14.10 on it. I completely wiped the drive and did a fresh install. Automatic, not manual.

After a couple of tries with only running Ubuntu, I am still having the same problem. It has to do with booting into the UEFI settings. My install worked fine until I booted into UEFI settings and then it not longer sees GRUB I guess. Again, boot repair isn't helping. I did get a boot repair report and I'll link to it below. I have tried following boot repair's advice of creating an EFI partition. After I do, it wants a boot partition created and seems to ignore the EFI partition I just created. I've tried following boot repairs instructions numerous times with not success.

If it matters at all, I had windows 10 TP installed before all this.

[http://paste.ubuntu.com/10630535/](http://paste.ubuntu.com/10630535/)

---

### Post by oldfred on 2015-03-20
You need to have the boot flag on the FAT32 partition for gparted to convert it to the efi partition. Or if using gdisk it is the code ef00. The actual gpt(GUID) code is a very long GUID code for an efi partition. Tools just use different short cuts to setting correct code.

       Surface Pro Ubuntu install:
[http://askubuntu.com/questions/265644/dual-boot-surface-pro-with-ubuntu](http://askubuntu.com/questions/265644/dual-boot-surface-pro-with-ubuntu)
[http://ubuntuforums.org/showthread.php?t=2183946](http://ubuntuforums.org/showthread.php?t=2183946)
[http://ubuntuforums.org/showthread.php?t=2209247](http://ubuntuforums.org/showthread.php?t=2209247)

---

### Post by canadian05 on 2015-03-21
So, after reading your response I tried something different. I didn't delete the existing efi partition and then make a new one. I just boot flagged the existing one from a live Ubuntu session. Then from that same live session, I ran boot-repair again.

However, it has now been un-hiding the boot menu for over 12 hours now. It says that this operation could take a few minutes, but I suspect 12 hours is a little past what should be expected. I tried stopping it, rebooting, and running boot-repair again but it just goes straight to "unhide boot menu" and keeps chugging a long.

---

### Post by oldfred on 2015-03-22
Some older systems had corrupted efi partitions. They were somehow read only. The solution for those was to backup everything, erase partition. Then create a new FAT32 partition with the boot flag and restore the efi files. But have not seen that or a similar issue lately.

---

