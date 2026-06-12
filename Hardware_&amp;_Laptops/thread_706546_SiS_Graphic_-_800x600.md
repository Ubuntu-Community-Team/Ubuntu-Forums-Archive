---
title: "SiS Graphic - 800x600?"
date: 2008-02-24
forum: Hardware &amp; Laptops
---

### Post by tplng on 2008-02-24
Yes again. Ubuntu switches to 800x600, but the Graphic Adapter should be able to display 1280x800. This is the output of lspci:
```

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

```

This is the xorg.conf: [http://ubuntuusers.de/paste/44199/](http://ubuntuusers.de/paste/44199/)
This is the xorg log file: [http://ubuntuusers.de/paste/44668/](http://ubuntuusers.de/paste/44668/)

Please help!

---

### Post by overdrank on 2008-02-24
> **tplng said:**
> Yes again. Ubuntu switches to 800x600, but the Graphic Adapter should be able to display 1280x800. This is the output of lspci:
```

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

```

This is the xorg.conf: [http://ubuntuusers.de/paste/44199/](http://ubuntuusers.de/paste/44199/)
This is the xorg log file: [http://ubuntuusers.de/paste/44668/](http://ubuntuusers.de/paste/44668/)

Please help!

Hi and welcome, you can try and reconfigure you xorg with this command in the terminal, located under applications, accessories. ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
If that fails then you can edit your xorg and change the default depth to 16 instead of 24 as this has helped other users. Example
```
Section "Screen"
85	Identifier "Default Screen"
86	Device "Standardgrafikkarte"
87	Monitor "Standardbildschirm"
88	DefaultDepth [COLOR="Red"]16[/COLOR]
89	SubSection "Display"
```
Use this command to edit your xorg ```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by tplng on 2008-02-25
I have it already done this, it doesn't even work with 4 bpp :(

---

