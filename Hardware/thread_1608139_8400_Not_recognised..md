---
title: "8400 Not recognised."
date: 2010-10-28
forum: Hardware
---

### Post by Yacoby on 2010-10-28
I recently put a 8400 into my computer so I could use a second screen. While this wasn't a problem setting it up on Windows, it is on Ubuntu. (I am using Ubuntu 8.04)

When I run "nvidia-settings" I get the message that "You do not appear to be running the NVIDIA X driver"

When I run nvidia-xconfig and restart, it won't load my desktop environment, just my dumps me at a terminal. It then (I may have run startx) puts me in basic gui, where I get a message about my graphics card not being recognised, and given the option to configure it.

When I enter my graphics card information manually and press test, the test fails.

I don't know if the output from lspci will help, but here it is anyway:
> yacoby@yacoby-desktop-ubuntu:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 VGA compatible controller: nVidia Corporation Unknown device 10c3 (rev a2)
03:00.1 Audio device: nVidia Corporation Unknown device 0be3 (rev a1)
04:07.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)


---

### Post by DirtyPC on 2010-10-28
> **Yacoby said:**
> I recently put a 8400 into my computer so I could use a second screen. While this wasn't a problem setting it up on Windows, it is on Ubuntu. (I am using Ubuntu 8.04)

When I run "nvidia-settings" I get the message that "You do not appear to be running the NVIDIA X driver"

When I run nvidia-xconfig and restart, it won't load my desktop environment, just my dumps me at a terminal. It then (I may have run startx) puts me in basic gui, where I get a message about my graphics card not being recognised, and given the option to configure it.

When I enter my graphics card information manually and press test, the test fails.

I don't know if the output from lspci will help, but here it is anyway:
Try looking on the NVIDIA website, i'm pretty sure they have Linux drivers on their website. :-)

---

### Post by Yacoby on 2010-10-28
I have the nvidia drivers from the repos installed. I have tried nvidia-glx and nvidia-glx-new.

However, it seems that installing the new Nvidia drivers worked. Thanks.

---

