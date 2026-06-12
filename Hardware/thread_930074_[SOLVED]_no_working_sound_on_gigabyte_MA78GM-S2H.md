---
title: "[SOLVED] no working sound on gigabyte MA78GM-S2H"
date: 2008-09-25
forum: Hardware
---

### Post by travm on 2008-09-25
Hi, I've got a gigabyte 780G motherboard, and I had a battle getting some video drivers to work, but now ive got the newest (8.9) ati driver working, but I have (and never did have) any sound at all.  I'm not really sure where to start with this one.  From the forums it seems like others have had this problem, but there doesnt seem to be a listed solution. 
Any ideas?

---

### Post by Crafty Kisses on 2008-09-25
What are the results of this command?
```
lspci
```

---

### Post by travm on 2008-09-25
output of lspci,
seems that my realtek chipset is not there...  what now?
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

```

I havn't check my TV, maybe i have sound output going through my HDMI cable.  But still, I need both working.

---

### Post by travm on 2008-09-25
So I figured out why linux has no sound...  
Since I am dual booting windows, I assumed that since sound works in windows that my speakers were correctly connected.  Turns out the windows driver was playing tricks on me by "detecting" which port had my speakers plugged in and routing the audio to that port.

plugging the speakers into the "speaker" port fixed my problem :)

So that was my defence, but yeah, sorry for this waste of space.  

in closing, i blame windows... :lolflag:

---

