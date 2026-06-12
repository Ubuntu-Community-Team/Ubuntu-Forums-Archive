---
title: "ubuntu/computer not detecting discrete graphic card"
date: 2012-01-24
forum: Hardware
---

### Post by Symo on 2012-01-24
Hi,
 
A few days ago I decided to upgrade my computer with a new graphics card (MSI N210 with GPU Nvidia GeForce 210) having previously just used the onboard graphics. After installation and connecting the card to the monitor cable there doesn't seem to be any signal: the screen is blank. I'm quite sure the card is correctly inserted into the PCI Express slot. 

On the box the card came in it says the minimum requirements are 350 W or greater (min 12V, 18A). On the computer power supply it states: > Output max power: 450 W
+3.3V, +5V Combined Load: 200W
+3.3V, +5V & +12V Combined Load: 430 W and the current ratings are: > +12V1: 14 A
+12V2: 16A
So maybe the current isn't enough? But the fan on the card is running so there is power there. The card requires no other power cable for it to function.

I've been into the BIOS and changed the setting 'Primary Graphics Adapter' to PCIE. I've removed all Nvidia graphic drivers and even the Nouveau driver and installed the specific driver for the graphics card from the Nvidia website, but still nothing. 

My lspci output
> 00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
[COLOR="Red"]00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2)[/COLOR]
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.2 Multimedia audio controller: nVidia Corporation MCP51 AC97 Audio Controller (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
04:08.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)

So it seems like the card isn't even detected. The VGA controller above is the chip on my mobo.
Any ideas?

---

### Post by Symo on 2012-02-13
Since last post I sent off for a new video card thinking it might be that which was faulty but the problem remains the same.

What reasons can there be for a discrete video card not being detected?

---

### Post by Yellow Pasque on 2012-02-14
Buggy BIOS? Is your BIOS up to date?

---

### Post by Symo on 2012-02-22
Yeah, it was a good guess - my BIOS has been a bit buggy, not wanting to always save any changes I made in it. So I updated it (without killing my computer which I'm pretty chuffed about) but the new video card is still not recognised.

So I'm thinking that either it's down to a fault in the PCI Express slot, or the card isn't compatible with my computer. (Or I guess that even the second card I got is faulty, though seems unlikely.)

---

