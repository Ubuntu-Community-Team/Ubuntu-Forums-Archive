---
title: "Can't detect PCIe RAID drive"
date: 2016-06-02
forum: Hardware
---

### Post by rijesh2 on 2016-06-02
Hi all,

Recently there has been an influx of the NVME PCIe ssds into the market. (samsung 950 M.2 ssd) and ubuntu has difficulty detecting them.

I am trying to detect the drive on a YOGA 900. Other folks have had this problem but have been able to change the sata mode in the bios from RAID to AHCI. The bios for the yoga 900 is locked.

Here are a few links of the solutions for an unlocked BIOS with advanced configuration options.

Someone was having the same problem with the dell XPS 13.
[https://bbs.archlinux.org/viewtopic.php?id=204629](https://bbs.archlinux.org/viewtopic.php?id=204629)
and here.
[http://askubuntu.com/questions/696413/ubuntu-installer-cant-find-any-disk-on-dell-xps-13-9350](http://askubuntu.com/questions/696413/ubuntu-installer-cant-find-any-disk-on-dell-xps-13-9350)
 
Here is another couple threads with the same problem and solution for a Dell Precision.
[http://superuser.com/questions/1022849/m-2-samsung-sm951-nvme-ssd-not-recognized-on-linux](http://superuser.com/questions/1022849/m-2-samsung-sm951-nvme-ssd-not-recognized-on-linux)
[http://askubuntu.com/questions/707494/primary-ssd-on-dell-precision-7510-cannot-be-detected-by-ubunt...]("http://askubuntu.com/questions/707494/primary-ssd-on-dell-precision-7510-cannot-be-detected-by-ubuntu-installer")
 
here is another thread indicating the need to disable RAID mode.

[http://www.tomshardware.com/answers/id-2771559/asus-z170-bios-detecting-s951-pcie.html](http://www.tomshardware.com/answers/id-2771559/asus-z170-bios-detecting-s951-pcie.html)


Now is there a solution for those who do not have access to the advanced setting in their BIOS?
I can detect the device in lspci:
```

00:17.0 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 21)
    Subsystem: Lenovo 82801 Mobile SATA Controller [RAID mode]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 16
    Memory at a12a0000 (32-bit, non-prefetchable) [size=32K]
    Memory at a12b6000 (32-bit, non-prefetchable) [size=256]
    I/O ports at 3080 [size=8]
    I/O ports at 3088 [size=4]
    I/O ports at 3060 [size=32]
    Memory at a1200000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: [d0] MSI-X: Enable+ Count=10 Masked-
    Capabilities: [70] Power Management version 3
    Capabilities: [a8] SATA HBA v1.0
    Kernel driver in use: ahci
    Kernel modules: ahci

```

The drive is not seen in /dev/mapper. The only thing in that folder is control.

---

### Post by st_ab on 2016-06-09
Did you have any luck so far?

---

### Post by oldfred on 2016-06-09
I think the issue may be just the installer. And that may be because based on older version of gparted? Bug supposedly fixed long time ago. See below.

Some have used newer gparted to partition in advance, then use Something Else to use those partitions.
 gparted should be at least version 0.24.0-1 to recognize NVMe devices
[http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php)
Filesystem support
[URL="http://ubuntuforums.org/showthread.php?t=2318570"]http://ubuntuforums.org/showthread.php?t=2318570

[/URL]
 Support for NVMe in grub-mkdevicemap fixed in 2014
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1275162](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1275162)
spec entry for nvme devices (UEFI v2.4A 9.3.5.22) 

[URL="http://ubuntuforums.org/showthread.php?t=2318570"]
[/URL]

---

### Post by st_ab on 2016-06-09
Neither the latest stable version of GParted Live nor the latest testing and stable version of Clonezilla are able to access the ssd :(

---

