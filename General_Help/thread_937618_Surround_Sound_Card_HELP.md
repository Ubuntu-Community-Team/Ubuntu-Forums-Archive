---
title: "Surround Sound Card HELP"
date: 2008-10-04
forum: General Help
---

### Post by Jaz969 on 2008-10-04
OK, so I've been trying night day to get this right. I'm using Wubi 8.04.1 to boot ubuntu on my PC. My sound card is a Creative X-Fi Extreme Audio. Works great on Windows, but I can't seem to get ubuntu to go surround sound with it. You see, I have my speakers plugged in as front left and right and my headset (with a mic) plugged in as the rear left and right. For a lil bit on ubantu I had sound only from my speakers, than I had it so that all the ubuntu noises were surround, but no other programs. So I was curious if someone could help me achieve this

---

### Post by Crafty Kisses on 2008-10-04
What are the results of this command?
```
lspci
```

---

### Post by Jaz969 on 2008-10-04
family@family-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA AHCI Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc RV380 [Radeon X600 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV380 [Radeon X600]
04:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller (rev 01)
05:02.0 Multimedia video controller: NEC Corporation Dual Tuner/MPEG Encoder (rev 0b)
05:04.0 Multimedia audio controller: Creative Labs SB Audigy LS
05:05.0 Communication controller: Conexant HSF 56k Data/Fax Modem
family@family-desktop:~$

---

### Post by Jaz969 on 2008-10-04
bump!

---

### Post by Jaz969 on 2008-10-04
bump

---

