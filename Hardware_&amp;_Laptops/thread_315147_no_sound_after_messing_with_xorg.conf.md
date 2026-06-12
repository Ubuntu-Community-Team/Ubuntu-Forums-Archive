---
title: "no sound after messing with xorg.conf"
date: 2006-12-08
forum: Hardware &amp; Laptops
---

### Post by zekopeko on 2006-12-08
i was installing radeon drivers on my 9600 so i could try beryl with AIGLX.
that went fine but now i have no sound.
the output of lspci:

00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 0 (rev c1)
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
02:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
02:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)

what could be the problem hear. it worked right out of the box since this is a well know chipset.
were could i have messed up?
i'm guessing that my playing with xorg.conf has nothing to do with this since that is the config for xserver aka graphics.
btw this is edgy

---

