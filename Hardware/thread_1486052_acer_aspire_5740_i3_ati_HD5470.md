---
title: "acer aspire 5740 i3 ati HD5470"
date: 2010-05-17
forum: Hardware
---

### Post by Patrock.nl on 2010-05-17
after years of working with ubuntu, and other *nix distro's i'm sticking with Ubuntu, Recently i bought myself a acer aspire 5740 with an intel i3 and build in ATI HD5470, i was hoping i could switch the built in I3 GPU and the ATI card, wich is not the case. is there a descent driver available for the ati card? i've tried all the offcial channels, and my card doesnt seem to be supported yet, this isnt the most pressing issue, whats buggin' me more is the fact that the wirreless driver doesnt seem to be getting along with the kernel, at random times the kernel crashes if i have wireless enabled, anyone else familiar with these problems?  i could really use a hand with this, just tell me what info you need, i can provide it, for everything else this is a perfect laptop, as long as you stay with win7, wich will remain my primairy OS cause of the graphic programs that i cant find suitable replacements for in *nix, ive tried installing hackintosh, hey, at least no windows, but to great regrets, need the d*mn kexts

[no need for newbie talk, tech talk is fine too :guitar: ]

appriciate your help!

---

### Post by Crafty Kisses on 2010-05-17
Hello, 

Your ATI card should be just fine. You can grab the ATI Catalyst Linux driver, and that should work, I personally don't use ATI, so I'm not too sure on how that card would work on Linux.

For your wireless issue, I need a bit more information, what are the results of the following?

```
lspci
lshw -C network
lsusb
```

---

### Post by Patrock.nl on 2010-05-21
thanks for the quick reply, here's the information you've requested, ive changed the username computername and mac adresses for obvious reasons,

the wirelless is disabled or else i get a kernel error, but you have the info it give's

> USER@COMPUTERNAME:~$ lspci
00:00.0 Host bridge: Intel Corporation Arrandale DRAM Controller (rev 12)
00:01.0 PCI bridge: Intel Corporation Arrandale PCI Express x16 Root Port (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 VGA compatible controller: ATI Technologies Inc Device 68e0
02:00.1 Audio device: ATI Technologies Inc Device aa68
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
05:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
ff:00.0 Host bridge: Intel Corporation QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Device 2d12 (rev 02)
ff:02.3 Host bridge: Intel Corporation Device 2d13 (rev 02)
USER@COMPUTERNAME:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetLink BCM57780 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 01
       serial: **MACADRRESS**
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.99 firmware=sb ip=**localIP** latency=0 multicast=yes
       resources: irq:32 memory:f0200000-f020ffff
  *-network DISABLED
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 01
       serial: **MAC ADRES**
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0300000-f030ffff
USER@COMPUTERNAME:~$ lsusb
Bus 002 Device 003: ID 04f2:b044 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
USER@COMPUTERNAME:~$ 

 

by the way, i'm now upgrading to 10.04, if these problems persist i will let you know in a couple of hours

ati card as mentioned ist working properly, as the ati drivers don't recognize a ati card, this was the reason and the wireless issue to find help. probably the 5470 doen'st have drivers for *nix yet, lets attack wirelless first :P



----------------------------------------------------------------------------------
after a clean install of ubuntu 10.04 i heavent received any problems regarding wireless, good connectivity, only differance with the problematic config as posted above is that the logical name has changed to wlan0, perhaps an updated driver module released in the last week?, wil keep this updated as for crashes and stability regarding wireless, 

for the ati mobility radeon 5470 it now properly identifies my screen, alowing me to set the resolution correctly,ubuntu prompts for an prioparty driver, its available, (bug: the downloading and installing driver window is named untitled window ;))looks like the beast has finaly awoken, thanks, apriciate the help offerded

UBUNTU

---

