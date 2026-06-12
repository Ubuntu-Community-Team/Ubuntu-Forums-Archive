---
title: "Compex modem"
date: 2009-08-17
forum: Installation &amp; Upgrades
---

### Post by ramesh20033 on 2009-08-17
Hi,

I am from India.Recently i installed Ubuntu in my computer.I had UT300RU Modem which was automatically configured and i was able to connect to the net.When the modem was changed to Compex,i am unable to connect to the net.I am giving the output of commands below.Can anybody help me in sorting out the problem.
lspci
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics Controller (CGC) (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 02)
01:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 01)

dmesg | grep 'eth' 
[    5.871804] e100: eth0: e100_probe: addr 0xd4000000, irq 11, MAC addr 00:c0:a8:f6:2f:a8
[    7.718236] Driver 'sd' needs updating - please use bus_type methods
[    7.719064]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[  186.997922] ADDRCONF(NETDEV_UP): eth0: link is not ready

Thanks in advance
Ramesh

---

