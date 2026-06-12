---
title: "intel pro 1000 82547EI Gigabit, no gigabit connections ever, only 100"
date: 2013-01-18
forum: Hardware
---

### Post by sdowney717 on 2013-01-18
Builtin to the motherboard.
This is a server motherboard S875PW1-E

02:01.0 Ethernet controller: Intel Corporation 82547EI Gigabit Ethernet Controller

I also dual boot with win7 and tried several cables. I even physically picked up the PC and put it right next to the gigabit switch with a known good short cat5e cable. It never connects at gigabit speed.

It is running the latest bios p18.

So, is it impossible to make work right?
Is there a way to force it?


```
scotts875@scotts875-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02)
00:03.0 PCI bridge: Intel Corporation 82875P/E7210 Processor to PCI to CSA Bridge (rev 02)
00:06.0 System peripheral: Intel Corporation 82875P/E7210 Processor to I/O Memory Interface (rev 02)
00:1d.0 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV515 PRO [Radeon X1300/X1550 Series]
01:00.1 Display controller: Advanced Micro Devices [AMD] nee ATI RV515 PRO [Radeon X1300/X1550 Series] (Secondary)
02:01.0 Ethernet controller: Intel Corporation 82547EI Gigabit Ethernet Controller
03:02.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
03:02.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
03:06.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Rage XL (rev 27)
03:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 01)
scotts875@scotts875-desktop:~$ 


```

---

### Post by Xanko on 2013-03-10
What do you get with 


```
sudo ethtool eth0
```

You may have to install ethtool

---

