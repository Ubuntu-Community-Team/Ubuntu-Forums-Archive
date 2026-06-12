---
title: "Uber frustration with atheros wifi"
date: 2009-09-29
forum: Installation &amp; Upgrades
---

### Post by Quarkangel7 on 2009-09-29
Hi I hope someone can help. I have an acer aspireone 150 that has extreme troubles with wireless. I have tried everything from wicd to ndiswrapper to madwifi with no luck. I even got a new bios and tried recompiling a tarball, which gave a make error 2

I am at my wits end with this and am ready to throw this thing in the trash.

Any help with the atheros wifi card would be helpful.

Thanks alot.

Here is the output

     description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.3 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

&#8216;auto loniface lo inet loopbackn&#8217;
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 02)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)
Bus 005 Device 003: ID 0c45:62c0 Microdia Pavilion Webcam
Bus 005 Device 002: ID 0930:6544 Toshiba Corp. 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Linux deusex-laptop 2.6.27-14-generic #1 SMP Mon Aug 31 13:01:41 UTC 2009 i686 GNU/Linux
[    1.245035] pnp: PnP ACPI: found 9 devices
[    2.434922] pcieport-driver 0000:00:1c.0: found MSI capability
[    2.435472] pcieport-driver 0000:00:1c.1: found MSI capability
[    2.436019] pcieport-driver 0000:00:1c.2: found MSI capability
[    2.436558] pcieport-driver 0000:00:1c.3: found MSI capability
[    2.791572] isapnp: No Plug & Play device found
[    2.924916] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.842817] hub 1-0:1.0: USB hub found
[    4.909636] No dock devices found.
[    4.956686] hub 2-0:1.0: USB hub found
[    5.065228] hub 3-0:1.0: USB hub found
[    5.169348] hub 4-0:1.0: USB hub found
[    5.292672] hub 5-0:1.0: USB hub found
[    6.205406] usb-storage: device found at 2
[   14.999465] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x0460)
[   20.097691] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62c0)
[   24.214965] lp: driver loaded but no devices found
[   30.416351] apm: BIOS not found.
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

 * Reconfiguring network interfaces...                                          /etc/network/interfaces:1: misplaced option
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:1: misplaced option
ifup: couldn't read interfaces file "/etc/network/interfaces"

---

