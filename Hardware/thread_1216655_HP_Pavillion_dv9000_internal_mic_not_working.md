---
title: "HP Pavillion dv9000 internal mic not working"
date: 2009-07-18
forum: Hardware
---

### Post by addiebk on 2009-07-18
I'm currently trying to get the microphone on my mom's computer to work, which it does not.  Yes, there are a lot of posts of this nature already, but I have a few different questions that I have not yet seen.

Most of the already-available posts on this topic have solutions such as "check to see if everything is unmuted."  When I open volume control and click preferences, I am told (from many different forum topics) to check the microphone capture box.  There is no such checkbox on this computer.

My options:
  Master
  PCM
  Docking Mic
  External Mic
  Internal Mic
  IEC958
  IEC958 Default PCM

This computer is running Jaunty Jackalope, after a clean install.

I have performed the steps outlined in this tutorial: [http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

as well as the multimedia and video how-to:
[http://ubuntuforums.org/showthread.php?t=766683&highlight=comprehensive+multimedia+video+howto](http://ubuntuforums.org/showthread.php?t=766683&highlight=comprehensive+multimedia+video+howto)

The results of running lspci in the terminal are:
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

I realize that this is probably a driver issue.  I currently have the latest NVidia driver on the computer (version 180), and to my knowledge, there isn't really an alternative that would work any better.

The main reason that I would like to get the microphone working is so that my family can use Skype on my mom's computer.  I could easily convince them to get a USB headset if I were sure that it would work with Ubuntu, which I am not.

So, my three questions, in summary:
  Is there some option I'm missing in volume control that would make this all easier?
  Is there some non-proprietary driver that would allow my microphone to work, or should I just hold out for that?
  Given the current resources available, would a USB headset work on this computer?

Thanks for your time!

*EDIT*  I borrowed a friend's external microphone (not USB; it used the microphone port on the computer) and it worked PERFECTLY without any fiddling.  So, I guess I answered my own question there.  :P

---

### Post by cespinal on 2009-08-18
bump... well, basically you solved part of the problem :)

Mics in these models are not being supported yet after year and a half this issue being reported.

---

### Post by cespinal on 2009-10-30
bump.... any solutions yet? how about the new release?

---

