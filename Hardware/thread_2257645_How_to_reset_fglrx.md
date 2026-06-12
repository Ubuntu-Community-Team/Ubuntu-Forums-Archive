---
title: "How to reset fglrx"
date: 2014-12-21
forum: Hardware
---

### Post by nickyforiasha on 2014-12-21
[COLOR=#333333][FONT=UbuntuRegular]My fglrx is messed up, it allows the mouse to be sent to the right as if there was a monitor there. Checking with amdcccle and the display settings, none of them tell me there is one. Looking at the xorg.conf file, i see it thinks that there is another monitor but there actually isn't one. Also for an obviously related reason, cccle doesn't allow me to enable crossfire because crossfire is not allowed when there are more then 1 monitors. I tried reinstalling fglrx but my setup is still here. How can I start fresh without having to reinstall Ubuntu for like the 40th time in the last 3 years?[/FONT][/COLOR]

---

### Post by Bashing-om on 2014-12-21
nickyforiasha; Hi ! Welcome to the forum.

The place for answers.

OK, We need to know what we are working with; and match the software to the firmware.
What graphics chip(s) are installed ?
Post back the outputs - Between Code Tags -  of these terminal commands:
```

lspci -nnk | grep -iA3 vga
sudo lshw -C display

```
To also see the driver (if any ) that is installed.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]a tale will be told
[/INDENT][/INDENT]

---

### Post by nickyforiasha on 2014-12-22
i have a radeon HD 5870 and a Radeon HD 5850. Heres the output of lspci:

01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Cypress XT [Radeon HD 5870] [1002:6898]
	Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Radeon HD 5870 Eyefinity&#8310; Edition [1002:0b00]
	Kernel driver in use: fglrx_pci
01:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Cypress HDMI Audio [Radeon HD 5800 Series] [1002:aa50]
--
02:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Cypress PRO [Radeon HD 5850] [1002:6899]
	Subsystem: ASUSTeK Computer Inc. Device [1043:0348]
	Kernel driver in use: fglrx_pci
02:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Cypress HDMI Audio [Radeon HD 5800 Series] [1002:aa50]


Heres the output of lshw:
  *-display               
       description: VGA compatible controller
       product: Cypress XT [Radeon HD 5870]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:51 memory:d0000000-dfffffff memory:fdfc0000-fdfdffff ioport:ee00(size=256) memory:fdf00000-fdf1ffff
  *-display
       description: VGA compatible controller
       product: Cypress PRO [Radeon HD 5850]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:52 memory:c0000000-cfffffff memory:fdcc0000-fdcdffff ioport:de00(size=256) memory:fdc00000-fdc1ffff


Another interesting thing i found in fglrx is that x.org.conf really thinks i have 2 screens. lasdt time i installed ubuntu, i removed the sectuion with the second screen manually and my comp wouldnt start. i know i could have booted liveusb and changed it back but i was too pissed off because all im getting linux are problems. i also tried opensuse and debian, and even more problems there. my programs wouldnt isntall even thought theyre compatible with the exact versions, amd driver i would press install and it insdtantly says driver installed but it didint install anything, and best of all, the power menu in debian dissapeared completely. lots of other problems. anyways heres xorg.conf from /etc/x11


Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	Screen         "aticonfig-Screen[1]-0" RightOf "aticonfig-Screen[0]-0"
EndSection


Section "Module"
EndSection


Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection


Section "Monitor"
	Identifier   "aticonfig-Monitor[1]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection


Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection


Section "Device"
	Identifier  "aticonfig-Device[1]-0"
	Driver      "fglrx"
	BusID       "PCI:2:0:0"
EndSection


Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


Section "Screen"
	Identifier "aticonfig-Screen[1]-0"
	Device     "aticonfig-Device[1]-0"
	Monitor    "aticonfig-Monitor[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

---

### Post by Bashing-om on 2014-12-22
nickyforiasha; Well;

Not finding any info to guide us for switchable ATI/ATI !!
Maybe switcheroo is an option ???
Be advised that 'switcheroo' is only available using the open source drivers.
And as well looks like it could be a challenge to set up .
What returns: - If anything at all -
```

cat /sys/kernel/debug/vgaswitcheroo/switch

```

see: [https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

I just can not say what might be a course of action.
[INDENT][INDENT]one of those times, I just do not know
[/INDENT][/INDENT]

---

### Post by nickyforiasha on 2014-12-22
fixed the issue, i just rolled back my x.org version. i made a backup with amdconfig --initial and i entered "gksudo nautilus /etc/X11/" in the terminal and took the original backup "xoeg.conf.fglrx-0" opened it with gedit, select all and copy. Then open the current "xorg.conf" deleted everything there and pasted. Then save and reboot and everything works perfectly. Sorry for the false alarm, usually I fix issues this simple myself but i was afraid of loosing the entire OS liek last time.

---

### Post by Bashing-om on 2014-12-22
nickyforiasha; Outstanding !

Wow, do you do good work . You are now the go to for this ATI/ATI switchable graphics situation.

As this is at an end:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT]

---

