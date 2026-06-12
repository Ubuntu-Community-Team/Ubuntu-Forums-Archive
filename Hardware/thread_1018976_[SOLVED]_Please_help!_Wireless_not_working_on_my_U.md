---
title: "[SOLVED] Please help! Wireless not working on my Ubuntu 8.10"
date: 2008-12-22
forum: Hardware
---

### Post by cmmckoy on 2008-12-22
Okay, I'm sorry if this has already been addressed in another thread, I've looked but can't seem to find it.

The issue that I'm having is that I can't use my wireless connection when using Ubuntu.  When I was using 8.4 it wasn't an issue, but when I updated to 8.10 it suddenly stopped working, it will not detect any wireless, according to the troubleshooting files I narrowed it down to my wireless being off on my laptop (there is a button that turns wireless on/off on my laptop), and that I need to go into Windows and make sure it hasn't been turned off.  However, when I go into windows (I have Windows Vista on my laptop as well) my wireless is on, automatically connects and everything.  What do I need to do in order to fix this problem?  Any help would be greatly appreciated.

---

### Post by pytheas22 on 2008-12-22
If you could please post the output of the following commands, it should help to figure out what you need to fix:
```

lshw -C Network
lspci -nn
lsusb
sudo iwlist scan
uname -m
dmesg | grep adio
```

---

### Post by cmmckoy on 2008-12-22
> **pytheas22 said:**
> If you could please post the output of the following commands, it should help to figure out what you need to fix:
```

lshw -C Network
lspci -nn
lsusb
sudo iwlist scan
uname -m
dmesg | grep adio
```

lshw -C network
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: 88E8071 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 15
       serial: 00:1d:72:3a:0b:a8
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A ip=192.168.1.102 latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 7e:04:3c:90:c7:b9
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


_______________________________________

lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS690 Host Bridge [1002:7910]
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx) [1002:7912]
00:04.0 PCI bridge [0604]: ATI Technologies Inc Device [1002:7914]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1) [1002:7915]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2) [1002:7916]
00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389]
00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a]
00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b]
00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 14)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS690M [Radeon X1200 Series] [1002:791f]
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8071 PCI-E Gigabit Ethernet Controller [11ab:436b] (rev 15)
05:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
0b:06.0 CardBus bridge [0607]: O2 Micro, Inc. OZ711SP1 Memory CardBus Controller [1217:7136] (rev 01)
0b:06.2 SD Host controller [0805]: O2 Micro, Inc. Integrated MMC/SD Controller [1217:7120] (rev 02)
0b:06.3 Mass storage controller [0180]: O2 Micro, Inc. Integrated MS/xD Controller [1217:7130] (rev 01)
0b:06.4 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. Firewire (IEEE 1394) [1217:00f7] (rev 02)

__________________________

lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0461:4d4b Primax Electronics, Ltd 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

________________________
iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

__________________________

uname -m
i686
______________________________

In regards to that last command, I'm not sure what to type, but with the other commands I posted exactly what resulted.

And thanks for the help, it's much appreciated. :D

---

### Post by pytheas22 on 2008-12-22
You have a Broadcom 4312 wireless card.  The driver for it changed between 8.04 and 8.10, which explains why it's not working for you now.  You probably just need to install firmware for the new driver and load it.

If you go to System>Administration>Hardware Drivers, is there an option to enable your wireless card?  If there is, please follow the instructions there.

If that doesn't work, we can get it working manually.  In that case, please tell me the output (in this order) of:
```

sudo modprobe b43
lshw -C Network
dmesg | grep -e b43 -e wlan
sudo rmmod b43
sudo modprobe wl
lshw -C Network
dmesg | grep -e wl -e eth1
```

The vertical line in commands like *dmesg | grep -e b43 -e wlan*, which is called a pipe, can usually be found above the 'enter' key, at least on most American keyboards.

---

### Post by cmmckoy on 2008-12-22
That did the trick, thank you very much.

I don't know why I didn't think of that earlier...I was in the Hardware Drivers thing recently since updating to update my video card...but I guess hindsight is 20/20...thanks again. :P

---

### Post by ross.u on 2008-12-22
what is the alternative method? i'm having the same problem and believe i have a broadcom card too. nothing but my video card shows up in hardware drivers.

---

### Post by cmmckoy on 2008-12-22
> **ross.u said:**
> what is the alternative method? i'm having the same problem and believe i have a broadcom card too. nothing but my video card shows up in hardware drivers.

Well I'm not sure what the alt method is, but if you post the output from the commands above he may be able to give you a more specific answer.

---

### Post by ross.u on 2008-12-22
> ross@ross-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1b:77:9b:db:e0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:24:77:ab:a3
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.101 latency=0 module=r8169 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 7e:4f:c5:18:f9:05
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
ross@ross-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8400M GS [10de:0427] (rev a1)
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
07:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
07:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
07:09.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
07:09.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
07:09.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)
ross@ross-laptop:~$ 
ross@ross-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8400M GS [10de:0427] (rev a1)
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
07:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
07:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
07:09.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
07:09.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
07:09.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)
ross@ross-laptop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 04f2:b015 Chicony Electronics Co., Ltd 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ross@ross-laptop:~$ sudo iwlist scan
[sudo] password for ross: 
Sorry, try again.
[sudo] password for ross: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

ross@ross-laptop:~$ uname -m
i686
ross@ross-laptop:~$ dmesg | grep adio
[   26.348135] iwl3945: Radio disabled by HW RF Kill switch
[   26.364068] iwl3945: Radio disabled by HW RF Kill switch
[  792.428999] iwl3945: Radio disabled by HW RF Kill switch
[  792.449660] iwl3945: Radio disabled by HW RF Kill switch
ross@ross-laptop:~$ 



Thanks in advance for your help, i'm going out of the country in january and wanted to make sure i can use wireless before i go.

---

### Post by pytheas22 on 2008-12-22
cmmckoy: glad it's fixed :)

ross.u: it actually looks like you have an Intel wireless card, not Broadcom, but that's not really relevant because the root of your problem is different.  The reason it's not working (according to the output you posted) is that the radio is disabled.  There should either be a physical button somewhere on your laptop that you use to toggle the wireless on and off, or a key combination to do the same thing (for example, Function+F2).  Do you know where this key is, and if you toggle it, can you connect to wireless networks?

There may also be an option in BIOS where you can force the wireless radio to always be on, which is another solution (but you save power by turning the radio off when you're not using wireless).

If you can't figure things out, please tell me your laptop model, as specifically as possible.

---

### Post by ross.u on 2008-12-22
I have an HP dv6500t that was purchased August 2007, and yes I have a wireless switch on the front of the laptop that doesnt change when i flip it on or off, the red light is always on and the wireless doesn't pick up in either position. I'll try the BIOS idea but if you have any solutions that would be wonderful.

---

### Post by cmmckoy on 2008-12-23
> **ross.u said:**
> I have an HP dv6500t that was purchased August 2007, and yes I have a wireless switch on the front of the laptop that doesnt change when i flip it on or off, the red light is always on and the wireless doesn't pick up in either position. I'll try the BIOS idea but if you have any solutions that would be wonderful.

Well I'm nowhere near as experienced in Ubuntu or Linux as some of the other people on these forums, I thought I'd do a little digging around the internet (one thing I am good at doing) to see if I could help with with your problem.

I came across a forum where a user installed Fedora on his DV6500t and was having similar problems with his wireless, his resolution was first re-ensuring that all of his OS drivers, etc. were fully updated, then going to [http://intellinuxwireless.org](http://intellinuxwireless.org) to get the driver information for his wireless card (I'm assuming that since you have the same model, the card is the same).  I'm not sure if this is an answer to your issue, but I didn't want to come back empty-handed.

Hope this helps, but I'd listen to anyone who actually knows what they're doing before anything else. :P

---

### Post by cmmckoy on 2008-12-23
oh, and according to the internets, your wireless card should be an Intel 4965AGN, if that helps any.

---

### Post by pytheas22 on 2008-12-23
ross.u: please try flipping the switch a few times to toggle the radio on and off, then immediately open a terminal, run the following command and post the output here:
```

dmesg | tail -50
```

That should help to figure out why the switch doesn't want to do anything.

Please also check your BIOS for any options related to the radio.

---

### Post by ross.u on 2008-12-23
ross@ross-laptop:~$ dmesg | tail -50
[   26.011768] iwl3945 0000:02:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[   26.012057] firmware: requesting iwlwifi-3945-1-lbm.ucode
[   26.348135] iwl3945: Radio disabled by HW RF Kill switch
[   26.348222] iwl3945 0000:02:00.0: PCI INT A disabled
[   26.363605] iwl3945 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   26.363775] iwl3945 0000:02:00.0: restoring config space at offset 0x1 (was 0x100102, writing 0x100106)
[   26.364068] iwl3945: Radio disabled by HW RF Kill switch
[   26.364138] iwl3945 0000:02:00.0: PCI INT A disabled
[   26.489241] NET: Registered protocol family 17
[   64.333841] CPU0 attaching NULL sched-domain.
[   64.333862] CPU1 attaching NULL sched-domain.
[   64.337140] CPU0 attaching sched-domain:
[   64.337151]  domain 0: span 0-1 level MC
[   64.337158]   groups: 0 1
[   64.337171] CPU1 attaching sched-domain:
[   64.337177]  domain 0: span 0-1 level MC
[   64.337182]   groups: 1 0
[   84.255847] NET: Registered protocol family 10
[   84.256972] lo: Disabled Privacy Extensions
[   95.048088] eth0: no IPv6 routers present
[  449.361297] ieee80211_crypt: registered algorithm 'NULL'
[  775.552064] ieee80211_crypt: unregistered algorithm 'NULL'
[  788.269152] cfg80211: Using static regulatory domain info
[  788.269167] cfg80211: Regulatory domain: US
[  788.269172] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  788.269180] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2700 mBm)
[  788.269188] 	(5170000 KHz - 5190000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[  788.269195] 	(5190000 KHz - 5210000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[  788.269201] 	(5210000 KHz - 5230000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[  788.269208] 	(5230000 KHz - 5330000 KHz @ 40000 KHz), (600 mBi, 2300 mBm)
[  788.269214] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (600 mBi, 3000 mBm)
[  788.269220] cfg80211: Calling CRDA for country: US
[  788.350533] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[  788.350540] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[  788.350648] iwl3945 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  788.350669] iwl3945 0000:02:00.0: setting latency timer to 64
[  788.350691] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[  788.392145] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[  788.393138] phy0: Selected rate control algorithm 'iwl-3945-rs'
[  792.420781] iwl3945 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  792.421314] firmware: requesting iwlwifi-3945-1-lbm.ucode
[  792.428999] iwl3945: Radio disabled by HW RF Kill switch
[  792.445767] iwl3945 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  792.449660] iwl3945: Radio disabled by HW RF Kill switch
[  813.684057] CE: hpet increasing min_delta_ns to 15000 nsec
[26897.146466] r8169: eth0: link down
[26899.129154] r8169: eth0: link up
[26900.158561] r8169: eth0: link down
[26901.991793] r8169: eth0: link up
[126479.493051] CE: hpet increasing min_delta_ns to 22500 nsec
ross@ross-laptop:~$

---

### Post by ross.u on 2008-12-23
oh and to answer the updated driver issue, honestly i'm about 3 weeks into making a switch to linux and couldn't figure out how to install it. Thanks to all for the help, I'm honestly really quite pleasantly surprised at the knowledge and responsiveness the ubuntu community has.

---

### Post by Coder543 on 2008-12-23
The way I am reading that (I leave possibility for my mistake) then the wireless card did re-enable momentarily then got cut off. Additionally, you left it in the *off* state. Perhaps, the *on* and *off* positions are swapped in Ubuntu? Or... something else is hapenning.

---

### Post by pytheas22 on 2008-12-23
The card may have been coming on and off successfully; I'm not sure based on the output that you posted.  It could be the case that the radio is being toggled on and off, but the light is staying the same color for some reason.  So please try the following tests:

1. flip the wifi switch, then run these commands and post the output:

```
sudo ifconfig wlan0 up
sudo iwlist scan
```

2. flip the switch a second time, and run these commands again:

```
sudo ifconfig wlan0 up
sudo iwlist scan
```

3. run these commands and post the output:

```
sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1
sudo iwlist scan
```

4. finally, hit the wifi switch one last time and run these commands again and post output:


```
sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1
sudo iwlist scan
```

This should help get to the bottom of things.

---

### Post by ross.u on 2008-12-23
strangely enough, even though im certain i've tried it in both positions, **that worked**, as embarassingly simple as that was. Thank you all so much for the help, i'm sorry that was so simple and I didn't realize it. Looking forward to being active in the community.

---

### Post by pytheas22 on 2008-12-23
Oh, good to hear (disregard the above post then).  Just in case anyone else comes upon this thread with the same problem, though, could you please clarify what exactly you did that made it work?  Do you just mean that flipping the switch again did the trick?

---

### Post by ross.u on 2008-12-24
Honestly, there's no way of telling, as i said im fairly sure that i had tried just flipping the switch before but any combination of what was suggested in other posts may have fixed that and i wasn't aware of it as my wireless switch was off.

---

