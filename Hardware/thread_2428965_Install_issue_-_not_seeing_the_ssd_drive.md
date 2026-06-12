---
title: "Install issue - not seeing the ssd drive"
date: 2019-10-11
forum: Hardware
---

### Post by porktree on 2019-10-11
I got a Dell 5500 recently, with the WD SN520 NVMe ssd drive.  Once I'd flattened it and put on Win10 I tried to install 19.04.  It boots fine into the installer, but the internal ssd drive is not seen.  I can also boot into Ubunto off the stick and still not see or mount the ssd drive.  I've been through the bios, disabling secure boot, setting uefi (boot stick was made with Rufus).  I also tried Fedora 30, and had the same issue.  I'm sure there's a hardware/bios thing I'm missing, but am at a loss.  Thanks.

---

### Post by oldfred on 2019-10-11
Dell typically needs UEFI update and if SSD, SSD firmware update.
Then it also needs drive setting changed from RAID/Intel RST to AHCI. But if dual booting with Windows you must first add AHCI drivers into Windows for it to work.

Dell Precision 5530
[https://ubuntuforums.org/showthread.php?t=2420905](https://ubuntuforums.org/showthread.php?t=2420905)
Dell 5230 with 3 m2 drives.
[https://ubuntuforums.org/showthread.php?t=2406057](https://ubuntuforums.org/showthread.php?t=2406057)
Dell Latitude 5490 M.2 PCIe SSD
[https://ubuntuforums.org/showthread.php?t=2405822](https://ubuntuforums.org/showthread.php?t=2405822)
 DELL Precision 5820 tower and NVMe M.2 front-panel SSD issues  Secure boot off, RAID on
[https://ubuntuforums.org/showthread.php?t=2381899](https://ubuntuforums.org/showthread.php?t=2381899)
Dell Precision 5820 with PCI NVME SSD UEFI update & SSD firmware update
[https://ubuntuforums.org/showthread.php?t=2402254](https://ubuntuforums.org/showthread.php?t=2402254)
Dell Inspiron 15 5567 AMDGPU-Pro driver causes a kernel panic  Jan 2017
[https://ubuntuforums.org/showthread.php?t=2347889](https://ubuntuforums.org/showthread.php?t=2347889)

---

### Post by porktree on 2019-10-11
After I started this thread I tried changing the bios from RAID to AHCI - which resulted in boot failure.  Changing it back to RAID required a few reboots but Win finally started.  I'm having trouble finding an AHCI driver for the Latitude 5500, but I'll keep looking.  Thanks for the info.

edit:
Success!

Here's what I had to do:
1 - Switch Windows to boot in Safe Mode
2 - Reboot, enter the bios, and switch to normal boot
3 - Reboot, and voila - Windows is running under AHCI
4 - Boot off the install stick and install Ubunto next to Windows

Thanks again for the help.

---

