---
title: "Ubuntu doesn't think my simpletech HD is a device"
date: 2008-04-16
forum: Hardware &amp; Laptops
---

### Post by jxn on 2008-04-16
I have seen a few quasi-related posts to this one, but my problem is slightly different.  I have a 350 GB unpowered (uses two USB ports, rather than separate power source) external HD from simpletech.  I had this drive working fine in my former setup (same machine, but I was using gentoo), and formated the filesystem to reiserFs.  I never had to do anything to get gentoo to recognize the device (in fact, udev + ivman mounted it flawlessly since the very first plug-in).

However, now, I'm trying to install ubuntu on this machine (I broke my old gentoo installation and don't have the time/patience to go through that install process again), and I need to get old files off of my /home/user partition and on to the external drive; however, the ubuntu livecd's (both the current stable and the new hardy heron betas) don't even recognize my drive's existence.  I've mounted just about everything available in /dev, and the drive should be working flawlessly, but I've had absolutely no luck.

Any help/ideas?

Thanks very much!

---

### Post by jxn on 2008-04-16
In case it's any assistance, here's the output of lsusb:

```
# lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000
```

and lspci as well, just in case:
```
# lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 11)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 11)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)
02:09.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
02:09.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
02:09.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
02:0d.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
02:0e.0 Multimedia video controller: Internext Compression Inc iTVC15 MPEG-2 Encoder (rev 01)
```

---

### Post by jxn on 2008-04-17
...it turns out, ubuntu livecds are not reading USB external hard drives at all... I hooked up another one, hoping to sidestep the issue, and it's not recognized as a device in any way, shape, or form, either....

---

### Post by jxn on 2008-04-23
Just in case somebody else runs into this problem and finds this thread; I had to eventually come up with another external drive to transfer my data to temporarily, and then installed ubuntu to my hard drive, hoping to overcome the problem of my simpletech external not being recognized.  I followed the advice of related threads, and never got the drive recognized.  For a while, i thought the drive had simply died, but I tried an Elive distro livecd, and the drive works flawlessly, so I've had to switch to that distribution for the time being (also, the drive works well from a gentoo live cd as well).  I'm not sure what's ubuntu's not doing right that does not allow it to recognize my drive (udev version's fault?  missing kernel modules?  I don't know, my elive has the same kernel version).  I hope that helps someone else.

---

### Post by jobbie007 on 2008-04-30
Thanks for the information. I think I am having the same problem and have been bashing my head against the wall on this. Ubuntu is not seeing my drive no matter what I do. Testdisk = no joy, ntfs-3g = nothing. I don't even get a /dev/sda of anything. i get entries in dmesg stating the following;

[ 1735.122854] scsi 4:0:0:0: Direct-Access     STECH    Simple Drive     8.14 PQ: 0 ANSI: 0
[ 1767.832993] sd 4:0:0:0: [sda] Spinning up disk......not responding...
[ 1886.025668] sd 4:0:0:0: [sda] READ CAPACITY failed
[ 1886.025674] sd 4:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 1886.025678] sd 4:0:0:0: [sda] Sense Key : Not Ready [current]
[ 1886.025681] sd 4:0:0:0: [sda] Add. Sense: Logical unit is in process of becoming ready
[ 1896.925166] sd 4:0:0:0: [sda] Test WP failed, assume Write Enabled
[ 1896.925172] sd 4:0:0:0: [sda] Assuming drive cache: write through
[ 1896.925221] sd 4:0:0:0: [sda] Attached SCSI removable disk
[ 1896.925259] sd 4:0:0:0: Attached scsi generic sg0 type 0

but that is it. I cannot get any further.

If anyone does get anything further on this then I would love to know.

New drive I think. Last time I buy a budget drive.

Martin:guitar:

---

