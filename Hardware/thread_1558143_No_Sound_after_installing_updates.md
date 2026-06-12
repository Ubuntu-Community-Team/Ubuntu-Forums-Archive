---
title: "No Sound after installing updates"
date: 2010-08-21
forum: Hardware
---

### Post by linuxyogi on 2010-08-21
Hi, the problem after installing updates there is absolutely no sound from any channels.

OS: Lucid 64


-----------------------------------------------------------------

**aplay -l**
aplay: device_list:235: no soundcards found...
-----------------------------------------------------------------


**lspci**
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:10.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:11.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation C68 [GeForce 7025 / nForce 630a] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control


**dpkg -l | grep "alsa"**
ii alsa-base 1.0.22.1+dfsg-0ubuntu3 ALSA driver configuration files
ii alsa-utils 1.0.22-0ubuntu5 ALSA utilities
ii bluez-alsa 4.60-0ubuntu8 Bluetooth audio support
ii gstreamer0.10-alsa 0.10.28-1 GStreamer plugin for ALSA
ii libsox-fmt-alsa 14.3.0-1.1build1 SoX alsa format I/O library


**head -n 1 /proc/asound/card*/codec#***
Codec: Realtek ALC662 rev1


 **cat /proc/asound/version**
Advanced Linux Sound Architecture [COLOR="Red"]Driver Version 1.0.23[/COLOR].
Compiled on Aug  6 2010 for kernel 2.6.32-24-generic (SMP)

Driver version here is 1.0.23 because I upgraded my alsa install using this script [http://ubuntuforums.org/showthread.php?p=6589810#post6589810]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810")

*After upgrading my alsa install using this script sound was coming fine. Its only the updates that I installed last night that has caused the problem. *

Here is what I updated -------------

linux-headers-2.6.32-24 (2.6.32-24.39) to 2.6.32-24.41
linux-headers-2.6.32-24-generic (2.6.32-24.39) to 2.6.32-24.41
linux-image-2.6.32-24-generic (2.6.32-24.39) to 2.6.32-24.41
linux-libc-dev (2.6.32-24.39) to 2.6.32-24.41


Please help.

---

### Post by Yellow Pasque on 2010-08-21
When you update the kernel, you must run the AlsaUpgrade script again (with -i option)

---

### Post by linuxyogi on 2010-08-21
> **Temüjin said:**
> When you update the kernel, you must run the AlsaUpgrade script again (with -i option)

Thanks for the info.
It worked.
Sound is working now.:D

Thanks a lot.

---

### Post by a.daniel on 2010-09-20
My sound problems after Upgrade to 2.6.32-24 were fixed by following the advice in [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/605519](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/605519)

> 
Actually, this appears to be a bug with permissions, I had to add myself to the audio group. I'm not sure what's causing it, but it doesn't appear to be kernel related.


---

