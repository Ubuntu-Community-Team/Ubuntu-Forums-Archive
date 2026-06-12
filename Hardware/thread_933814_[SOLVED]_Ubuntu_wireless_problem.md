---
title: "[SOLVED] Ubuntu wireless problem"
date: 2008-09-29
forum: Hardware
---

### Post by inxygnuu on 2008-09-29
My Atheros wireless card won't work. I know there are a ton of people asking this, but haw do I get it to work? My Netgear software won't work, because you can't run .exe files. Any ideas or simple(simpler) ideas?

---

### Post by pytheas22 on 2008-09-30
Please open a terminal, run the following commands and post the output here:
```

lspci -nn
lshw -C Network
uname -m
```

With that information, we can find instructions on getting your card to work.

---

### Post by inxygnuu on 2008-09-30
here are my specs:

00:00.0 RAM memory [0500]: nVidia Corporation MCP67 Memory Controller [10de:0547] (rev a2)
00:01.0 ISA bridge [0601]: nVidia Corporation MCP67 ISA Bridge [10de:0548] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation MCP67 SMBus [10de:0542] (rev a2)
00:01.2 RAM memory [0500]: nVidia Corporation MCP67 Memory Controller [10de:0541] (rev a2)
00:01.3 Co-processor [0b40]: nVidia Corporation MCP67 Co-processor [10de:0543] (rev a2)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP67 OHCI USB 1.1 Controller [10de:055e] (rev a2)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP67 EHCI USB 2.0 Controller [10de:055f] (rev a2)
00:04.0 USB Controller [0c03]: nVidia Corporation MCP67 OHCI USB 1.1 Controller [10de:055e] (rev a2)
00:04.1 USB Controller [0c03]: nVidia Corporation MCP67 EHCI USB 2.0 Controller [10de:055f] (rev a2)
00:06.0 IDE interface [0101]: nVidia Corporation MCP67 IDE Controller [10de:0560] (rev a1)
00:07.0 Audio device [0403]: nVidia Corporation MCP67 High Definition Audio [10de:055c] (rev a1)
00:08.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Bridge [10de:0561] (rev a2)
00:09.0 IDE interface [0101]: nVidia Corporation MCP67 AHCI Controller [10de:0550] (rev a2)
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP67 Ethernet [10de:054c] (rev a2)
00:0c.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Express Bridge [10de:0563] (rev a2)
00:0d.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Express Bridge [10de:0563] (rev a2)
00:12.0 VGA compatible controller [0300]: nVidia Corporation GeForce 7150M [10de:0531] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
02:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
02:05.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
02:05.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
02:05.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
02:05.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)
evan@evan-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:95:10:70
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=xxx.xxx.x.xx latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0

---

### Post by jcathey on 2008-10-01
First click on the start menu->settings-> hardware drivers and uncheck anything that has to do with Atheros (including atheros hal).

Download the latest madwifi drivers from madwifi and then untar them.  Open a terminal in as root in the untarred directory.  Then run the command make (NOTE:  you must have the package build-essentials for this to work properly).  Next run the command "make install"  If this finishes without erros run the following commands:

modprobe ath_pci
modprobe wlan_scan_sta

Then add ath_pci and wlan_scan_sta to the end of the file located at /etc/modules (this will make it so you do not have to insert these commands everytime you reboot.)

Reboot your laptop and you should be in business.

Hope this helps,

Jeremy

---

### Post by pytheas22 on 2008-10-01
> Download the latest madwifi drivers from madwifi and then untar them

Actually I don't think that this card is supported by old madwifi (i.e. the module ath_pci).  Instead I think that you need ath9k to get it to work; old madwifi doesn't support this device (PCI ID 168c:001c).

Please follow the instructions in [this post]("http://ubuntuforums.org/showthread.php?t=874097"), which will allow you easily to compile ath9k.  After that, your card should work.  If it still doesn't, please reboot, then post the output of these commands:
```

lsmod | grep ath
sudo modprobe ath9k
lshw -C Network
dmesg | grep -e ath -e wlan
sudo iwlist scan
```

---

