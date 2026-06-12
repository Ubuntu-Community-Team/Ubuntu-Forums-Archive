---
title: "SD card reader not working on Lenovo Yoga 2 Pro (Ubuntu 15.10)"
date: 2016-03-21
forum: Hardware
---

### Post by matej-kovacic on 2016-03-21
Hi,

I have Ubuntu 15.10, with the following kernel:

4.2.0-34-generic #39-Ubuntu SMP Thu Mar 10 22:13:01 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

When I insert SD card into card reader, nothing happens. sudo sfdisk -l does not show the device.

Here is lspci output:
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 0b)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 0b)
00:04.0 Signal processing controller: Intel Corporation Device 0a03 (rev 0b)
00:14.0 USB controller: Intel Corporation 8 Series USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation 8 Series HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 1 (rev e4)
00:1d.0 USB controller: Intel Corporation 8 Series USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation 8 Series LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 8 Series SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 8 Series SMBus Controller (rev 04)
00:1f.6 Signal processing controller: Intel Corporation 8 Series Thermal (rev 04)
01:00.0 Network controller: Intel Corporation Wireless 7260 (rev 6b)

However, card reader has been working with previous version of Ubuntu, so it could be a kernel problem?

I also tried to modprobe sm_ftl and rtsx_usb, but no success either...

---

### Post by matej-kovacic on 2016-03-21
OK, it seems the problem is with SD card - it seems it is broken.

---

