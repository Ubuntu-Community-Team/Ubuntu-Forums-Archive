---
title: "via chipset + kernel &gt; 2.6.35 issues"
date: 2012-03-09
forum: Hardware
---

### Post by maestrobwh1 on 2012-03-09
Is this a bug?

All hardware works will all ubuntu kernels at least from Ubuntu 8.10 until Ubuntu 10.10, Maverick with 2.6.35-32. via_agp HAS to be blacklisted in /etc/modprobe.d/blacklist.conf for all things to work.

Natty kernel will boot from USB drive (as installed os, not just from usb image) but no wifi or sound.

Oneric with 3.0.0-16 will NOT go past loading all hardware, as it drops to busybox and /dev/sdbX can't be found: HDIO_ something error basically not being able to find root device.  It partially boots then it appears that usb is blocked by something.  It still boots if I use the above Maverick kernel. It WILL boot from iso image with xforcevesa.

I transferred the setup to a partition on my hard drive and 3.0.0-16 boots but wifi and sound don't work although once desktop is up, usb drives are recognized.  Booting with xforcevesa and I also tried booting with via_agp.blacklist=yes which works with the latest puppy linux kernel that showed the same behavior.  Sound and wifi work with puppy slacko this boot option.

I cut and pasted some relevant hardware listing from lspci.  It shows the hardware being present.

ALL of this SHOULD work with the 3.0.0-x kernels according to my research.

02:01.0 Audio device: VIA Technologies, Inc. VT8237A/VT8251 HDA Controller (rev 10)
03:04.0 Ethernet controller: Atheros Communications Inc. AR5413 802.11abg NIC (rev 01)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 90)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 90)
00:00.0 Host bridge: VIA Technologies, Inc. CX700/VX700 Host Bridge (rev 03)
00:11.0 ISA bridge: VIA Technologies, Inc. CX700/VX700 PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. CX700/VX700 Internal Module Bus
00:13.0 PCI bridge: VIA Technologies, Inc. CX700/VX700 Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. CX700/VX700 PCI to PCI Bridge
01:00.0 VGA compatible controller: VIA Technologies, Inc. CX700/VX700 [S3 UniChrome Pro] (rev 03)

I am willing to post whatever boot log files to help get this resolved, I just need to know where to look as the boot process is still something I don't have a great understanding of even after using Ubuntu for 6 years.  If we find it is a bug with the kernel configuring something with the VIA chipset as I suspect, I will open one. 

Additionally, the openchrome driver does work in xorg.  I even get 3D with Ocelot and this did not happen with previous releases.

---

