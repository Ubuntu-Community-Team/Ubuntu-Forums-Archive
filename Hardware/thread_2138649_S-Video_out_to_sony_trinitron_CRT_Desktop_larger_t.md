---
title: "S-Video out to sony trinitron CRT Desktop larger than view area."
date: 2013-04-24
forum: Hardware
---

### Post by uncleBez on 2013-04-24
Not sure this is the correct section to post this question.

I had this working perfectly on other hardware. I upgraded my whole system, mother board, cpu, graphics card.
In fact I just swapped my hard drive from one machine to another.
The s-video out is display to the TV but with this new hardware the 'desktop' is larger than the TV screen.
This happens in the different window managers, unity, xfce and xbmc.
I have tried changing resolutions, the lower resolutions appear to just make the problem worse.
I am using proprietary Nvideo drivers, and have drive a couple different versions, all with the same effect.

I am using DISTRIB_RELEASE=11.10

Here is the output of my lspci

$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
**02:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)**

Any ideas welcome..

Any more information needed just ask.

Thanks!

---

### Post by uncleBez on 2013-04-28
found similar thread here [http://ubuntuforums.org/showthread.php?t=1590441](http://ubuntuforums.org/showthread.php?t=1590441) although the recommended solution does not
work for me.

---

