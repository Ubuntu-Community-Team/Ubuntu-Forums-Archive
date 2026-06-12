---
title: "Graphics acceleration"
date: 2009-12-30
forum: Hardware
---

### Post by betacheer on 2009-12-30
I am using Intel Integrated Graphics card e.g Intel Extreme Graphics 2 (If you need it I will give you a more info). And I am missing hardware graphics acceleration. I think this graphics card might do some acceleration but I don't know how. Anyone help me please?

Best regards and happy new year wishes Betacheer.

TXH

---

### Post by RedSingularity on 2009-12-30
Did you look in 

System>Admin>Hardware Drivers?

---

### Post by betacheer on 2009-12-30
Yes I looked but nothing :(

---

### Post by RedSingularity on 2009-12-30
Post the output of 

lspci

---

### Post by sarthorks on 2009-12-30
I am having a similar problem, although i dont remember the name of my Intel Graphics card now.

lspci:
```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
08:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
08:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
08:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
08:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

```

There is nothing in the hardware drivers for me as well.

Thanks.

---

### Post by betacheer on 2009-12-30
Here It IS:

```
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
03:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
03:0c.0 SCSI storage controller: LSI Logic / Symbios Logic 53c895 (rev 02)
```

---

### Post by RedSingularity on 2009-12-30
@ sarthorks

do sudo apt-get install xserver-xorg-video-intel

Reboot and see if you have acceleration.

---

### Post by betacheer on 2009-12-30
May I do it too?

---

### Post by RedSingularity on 2009-12-30
@ betacheer

You do the same

 sudo apt-get install xserver-xorg-video-intel

---

### Post by betacheer on 2009-12-30
It tells me that I have it installed already. Is this graphics so low accelerated because I don't see any acceleration. Countert Strike 1.6 is stuttering on it :D. Any other idea?

---

### Post by RedSingularity on 2009-12-30
Post the output of 

cat /etc/X11/xorg.conf

---

### Post by sarthorks on 2009-12-30
Same with me, newest version is already installed.

cat /etc/X11/xorg.conf:
```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

```

---

### Post by RedSingularity on 2009-12-30
In the part that says

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

```

Edit it to look like this

```
Section "Device"
	Identifier	"Configured Video Device"
       Driver          "intel"
EndSection

```

Then reboot.

---

### Post by sarthorks on 2009-12-30
Could you tell me a nice way to check if hardware acceleration is working?

---

### Post by RedSingularity on 2009-12-30
> **sarthorks said:**
> Could you tell me a nice way to check if hardware acceleration is working?

Right click your desktop and click "Choose desktop background".  Then go to the visual effects tab and select "Normal".  If you can do that then acceleration is working.

---

### Post by sarthorks on 2009-12-30
Extra too works for me in Hardy.
But in Karmic, using Live USB, extra gives a problem sometimes.

I guess I don't need to add "video      intel" line then, eh?

Thanks a lot anyway!

---

### Post by yakupciftci on 2009-12-30
i cant open that file cat /etc/X11/xorg.conf what is code?

---

### Post by RedSingularity on 2009-12-30
> **yakupciftci said:**
> i cant open that file cat /etc/X11/xorg.conf what is code?

You sure you are typing it exactly this way?

cat /etc/X11/xorg.conf

---

### Post by betacheer on 2009-12-31
It don't work for me too...

---

### Post by yakupciftci on 2009-12-31
it says no such file

---

### Post by RedSingularity on 2009-12-31
To create that file look at [this](http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html)

---

