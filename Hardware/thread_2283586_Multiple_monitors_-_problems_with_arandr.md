---
title: "Multiple monitors - problems with arandr"
date: 2015-06-23
forum: Hardware
---

### Post by nick196 on 2015-06-23
Hi-

I'm trying to setup an extended desktop in xubuntu 14.04.2 LTS with 2 monitors, a 17 inch and a 19 inch. I have an integrated graphics card on my motherboard and I have an nVidia 405 card installed with a DVI to VGA adapter attached as well. I installed arandr and tried to set it up with the two monitors. Photo of how it turned out: [http://i.imgur.com/wD6iS97.jpg](http://i.imgur.com/wD6iS97.jpg)

As you can see, the monitor on the left (coming from the DVI to VGA on my discrete card) is unusable. I've flipped the two monitors using arandr, and that doesn't change anything. I've tried using the other monitor on the discrete card, and that produces the same results. I've messed around with the "Display" options found in the xubuntu settings menu and can't make any progress there either. 
Results of lspci: 
00:00.0 RAM memory: NVIDIA Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: NVIDIA Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: NVIDIA Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: NVIDIA Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB controller: NVIDIA Corporation MCP61 USB 1.1 Controller (rev a3)
00:02.1 USB controller: NVIDIA Corporation MCP61 USB 2.0 Controller (rev a3)
00:04.0 PCI bridge: NVIDIA Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: NVIDIA Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: NVIDIA Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: NVIDIA Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: NVIDIA Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 405] (rev a2)
02:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)

Any suggestions on how to get rid of this craziness? I can post the xrandr -q output if that helps.

---

### Post by ajgreeny on 2015-06-23
What graphics driver are you using for the nvidia card?

I don't have and have never used an nvidia card, so I am not sure which driver is appropriate for your GT218 (GeForce 405), but if you haven't done so already haver a look in Additional Drivers to see if one is recommended, and if that still does not help, come back again.

---

