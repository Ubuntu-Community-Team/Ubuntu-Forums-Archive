---
title: "Dell 2400 Desktop effects."
date: 2009-12-02
forum: Hardware
---

### Post by Pestilent on 2009-12-02
Dell 2400, installed 9.10 and went to setup visual effects and received an error. Tried all I found in the forums with no luck but there is one issue I'm not certain about. Dell 2400 comes with onboard vid that CAN NOT be turned off in the bios. (There is no update for flashing them and fixing that issue) I am running a PCI vid card, could they be conflicting with one another? 

jafo@jafo:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 Display controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
01:04.0 PCI bridge: Pericom Semiconductor PI7C9X110 PCI Express to PCI bridge (rev 04)
01:06.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
01:06.1 Input device controller: Creative Labs SB Live! Game Port (rev 08)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)


Second entry and last entry in the list. Any ideas?



Used 
"mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager"
to bypass the blacklist and so far so good, so I'll assume it wasn't a conflict with the two adapters but with my primary video itself.

---

