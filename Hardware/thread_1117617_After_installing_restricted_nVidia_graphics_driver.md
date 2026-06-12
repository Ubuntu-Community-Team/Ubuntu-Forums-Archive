---
title: "After installing restricted nVidia graphics driver then rebooting, screen is blank"
date: 2009-04-06
forum: Hardware
---

### Post by blue carrot on 2009-04-06
Hey guys,
I've just installed Ubuntu 8.10 on my brand new system. 

I was (and still am) having the problem that the highest screen resolution I can get is 800x600, which is way too large and fuzzy for me. 

So I figured that I'd install the restricted graphics driver (177) for the onboard nVidia graphics. I did this and then when I reboot, the screen is entirely blank when the system restarts (but only when the desktop actually loads). 

To fix it I have to press esc during booting and then do a recovery start and select 'Try to fix X server'. This then uninstalls the driver and takes me back down to 800x600 screen resolution.

Can anyone help?

Also does this belong in absolute beginner talk? I tried searching for the solution to this but I couldn't find any with the same problem of the blank screen.

---

### Post by blue carrot on 2009-04-06
bump

---

### Post by krakk2k on 2009-04-06
is your card agp?

---

### Post by blue carrot on 2009-04-07
sorry, I don't know what AGP means. but checking the user manual for the mother board, I see that it is a nvidia GeForce 7 Series Shader model 3.0

---

### Post by krakk2k on 2009-04-07
> **blue carrot said:**
> sorry, I don't know what AGP means. but checking the user manual for the mother board, I see that it is a nvidia GeForce 7 Series Shader model 3.0

ok type "lspci" into terminal and post the results here!

---

### Post by blue carrot on 2009-04-07
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
**00:12.0 VGA compatible controller: nVidia Corporation GeForce 7050 PV / nForce 630a (rev a2)**
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

---

### Post by blue carrot on 2009-04-10
Still haven't found a solution. Can anyone help?

---

### Post by mrjawbones on 2009-04-19
I'm having the exact same problem, and after doing some research, apparently adding the line

Option "UseDisplayDevice" "DFP"

to the "Screen" section of your xorg.conf file is supposed to resolve it.  Blue Carrot, this may work for you, give it a try.  I've seen numerous posts from people who claim this has fixed the problem, but unfortunately it didn't work for me.  I have a Dell Latitude E6500 with an nVidia Quadro NVS160M.  I hope someone has another suggestion because I'm pretty much out of ideas at this point.

---

