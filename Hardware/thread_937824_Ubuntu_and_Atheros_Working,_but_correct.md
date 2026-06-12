---
title: "Ubuntu and Atheros: Working, but correct?"
date: 2008-10-04
forum: Hardware
---

### Post by mbott on 2008-10-04
I'm in need of an education when it comes to Ubuntu and my Compaq Presario C700.  So far, I've seemed to be able to keep the wireless functioning, but I really don't understand why.  Here is what I'm working with:

root@mlaptop:/home/mbott# lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)
02:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)


root@mlaptop:/home/mbott# lshw -C Network
  *-network               
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wifi0
       version: 01
       serial: 00:1e:4c:b1:ba:51
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.2.4 latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:1b:38:e7:55:ff
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s

root@mlaptop:/home/mbott# uname -m
i686

My concern is that an update/upgrade will disable the wireless and I won't be able to figure out what happened and what to correct.

TIA

-- 
Mike

---

### Post by pytheas22 on 2008-10-04
How did you get the card working in the first place?  You probably compiled the latest madwifi from source, right (I think that's the only way to get your chipset working in Hardy, because the default version of madwifi on Hardy doesn't support your card)?

If you compiled madwifi from source, then upgrading your kernel would probably break your wireless, because the wireless module (named 'ath_pci') needs to be built against the particular kernel that you're running.  So you should just keep the madwifi source code or the script that you used on hand so that you can recompile the wireless driver whenever you update your kernel.  It should only take a few seconds to recompile madwifi against a newer kernel, once you figure out how to do that.

Otherwise, beyond kernel upgrades, nothing should cause problems for your wireless card.

The kernel in Intrepid should support your card out-of-the-box, so if you upgrade to that version of Ubuntu, you should not need to worry about this anymore.

---

### Post by mbott on 2008-10-06
> **pytheas22 said:**
> Otherwise, beyond kernel upgrades, nothing should cause problems for your wireless card.

The kernel in Intrepid should support your card out-of-the-box, so if you upgrade to that version of Ubuntu, you should not need to worry about this anymore.

This was the underlying concern that prompted me to ask.  Kernel upgrades did cause me to re-compile.

I'm hoping Intrepid does support the card out of the box as this would remove some support effort on my part.

Thanks!

-- 
Mike

---

