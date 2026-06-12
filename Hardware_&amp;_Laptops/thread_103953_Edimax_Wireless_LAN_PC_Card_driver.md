---
title: "Edimax Wireless LAN PC Card driver"
date: 2005-12-15
forum: Hardware &amp; Laptops
---

### Post by spark888 on 2005-12-15
Hi All!

I just tested the Ubuntu 5.10 live cd on my old Toshiba tecra 9000 notebook pc. Everything worked fine except the Edimax Wireless LAN PC card (EW-7107PCg). Ubuntu can't seem to detect the hardware. Do i need to install a device driver for this? If so, i would appreciate any help on where to get the driver.

Thanks!

---

### Post by Lambert on 2005-12-15
Run these commands and post out put here.

lspci -v

sudo lshw -C network

If you know what part is your wireless card you can just post those sections.

lspci will tell what chipset you card has

lshw will tell if there is a driver in breezy that is allocating to the device. Some of edimax uses ralink so it's possible there's a driver.

---

### Post by spark888 on 2005-12-15
Hi Lambert!

I appreciate the quick response.

This is the output of the 'lspci -v' command:

0000:07:00.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn]  INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
        Subsystem: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
        Flags: medium devsel, IRQ 11
        I/O ports at 4800 [disabled] [size=32]
        Memory at 11000800 (32-bit, non-prefetchable) [disabled] [size=32]
        Memory at 11000000 (32-bit, non-prefetchable) [disabled] [size=2K]
        Capabilities: <available only to root>

and this is the oupput of the 'lshw -C network' command:

ubuntu@ubuntu:~$ lshw -C network
  *-network
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 41
       serial: 00:00:39:d9:68:a1
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 1 00bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=e100 driverversion =3.4.8-k2-NAPI duplex=half firmware=N/A link=no multicast=yes port=MII speed=10M B/s
       resources: iomemory:ff9ff000-ff9fffff ioport:df40-df7f irq:11
  *-network UNCLAIMED
       description: Ethernet controller
       product: [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
       vendor: Linksys, A Division of Cisco Systems
       physical id: 1
       bus info: pci@07:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       resources: iomemory:11000800-1100081f iomemory:11000000-110007ff irq:11

It looks like breezy doesn't have a driver for this device. I would need further help in interpreting the output. Thanks a lot!

---

### Post by Lambert on 2005-12-15
Looks like you'll need to use something called ndiswrapper to make the windows driver work for your device. I don't see or know of a native driver. There's a link in my signature that will take you to the ubuntu wiki with ndiswrapper instructions.

---

### Post by spark888 on 2005-12-15
Thanks for your help. I'll check out the link on your sig.

---

