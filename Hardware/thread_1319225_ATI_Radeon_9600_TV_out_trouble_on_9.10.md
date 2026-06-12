---
title: "ATI Radeon 9600 TV out trouble on 9.10"
date: 2009-11-08
forum: Hardware
---

### Post by lukacs on 2009-11-08
Hi!

I am totally new ubuntu user - having 9.10 just upgraded from 9.4.
I am having troubles with my ATI radeon 9600 Tv out card. The cards works okay but I want to enable tv-out and for that reason had downloaded a proproetary driver from ATi - ati-driver-installer-9-10-x86.x86_64.run - installed it via terminal but after rebooting I still have no responce from ATI Catalyst control center - it says 'no ATI graphic driver installed' nevertheless the installation finished successfully.
Looking to System-Administration-Hardware Drivers tells me that I do not have any proprietary drivers installed.
Had tried to install the drivers from Synaptic Pakcage Manager - same story - nothing had been activated.
lspci shows me:
00:00.0 Host bridge: nVidia Corporation nForce2 IGP2 (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
02:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]
02:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary)


Could anybody tell me where should I dig to be able to use the TV-out?
Maybe there is another workaround?

---

### Post by Quarkrad on 2009-11-22
Sorry - this is a bit off topic.  I have got in all sorts of trouble trying to get an ATI driver installed on my 9.10 for my Radeon 9600 card.  I just cannot do it - how did you manage to get it working and have the system recognise it as an ATI card?  If you look at **System/Administration/Hardware Drivers** does it show you have an ATI card?

---

### Post by lukacs on 2009-11-22
no, drivers window is not showing anything specific - so i believe i have generic driver installed.
i did nothing to install them - everything got ip at first time i'd boot

---

