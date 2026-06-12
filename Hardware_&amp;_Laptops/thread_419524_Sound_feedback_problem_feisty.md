---
title: "Sound feedback problem feisty"
date: 2007-04-23
forum: Hardware &amp; Laptops
---

### Post by SnoWDoGJDC on 2007-04-23
I'm having this weird problem on feisty that appeared some time after installing it (i think during one of the updates). Basically the input from the built in mic on my laptop is sent straight to my speakers. The only way to stop this is to mute the volume on the mic (and then i can't use skype or anything) and on top of that it un-mutes it again when i re-boot.
I'm using Feisty (upgraded to full version from beta 1) on an ASUS m6va laptop.
Also the boot hangs for about 20seconds when its enabling sound, once it's got past it then the mic feedback problem starts (i can tap the mic and hear it through the speakers)
All help is welcome. Note that otherwise sound output works fine.

lspci:
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
01:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
01:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
01:01.2 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
01:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
01:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 03)
01:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
03:00.0 VGA compatible controller: ATI Technologies Inc M26 [Radeon Mobility X700]

---

### Post by CitricAcid on 2007-04-25
Hello!
I have similar problem. But I did not test my mic. After installation of Feisty volume icon (that one near the clock) was set to line-in instead PCM. That was not a problem but using hotkeys for volume up/volume down line in volume was changing. How to fix this?

I have ASUS a3hf laptop.

-- CitricAcid


PS. That problem did not appear on Ubuntu 6.06 or 6.10. All systems were installed from CD (not from upgrade utility).

---

### Post by SnoWDoGJDC on 2007-04-26
I seem to have fixed this, but its not a great hack, i changed the mode from 2ch to 6ch in the volume control (needed to enable view of all the extra options). But if i change it back to 2 channel the input from the mic goes through the speakers again, and i still don't know why.

---

### Post by CitricAcid on 2007-04-26
Unfortunately it seems to be a problem on laptops (only ASUS?). I have installed Feisty on my desktop and there is no such problem at all.

---

