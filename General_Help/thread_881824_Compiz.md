---
title: "Compiz"
date: 2008-08-06
forum: General Help
---

### Post by adamant715 on 2008-08-06
Yet gain help with compiz, ok I selected my driver (I have no idea how) and the resoloution got huge. I fixed that and then I tryed to enable compiz. It didnt work. So what I&#7743; saying is, does anybody know a way that  I can install an intel driver for my gfx card? I looked everywhere. Please help is very much appreciated. And when I look at hardware drivers it says none are installed.

---

### Post by tuxxy on 2008-08-06
Did you try system > admin > hardware drivers

---

### Post by adamant715 on 2008-08-06
Yea, it says none are installed.

---

### Post by dannyboy79 on 2008-08-06
post lspci results so we know what gfx card you're using.

---

### Post by adamant715 on 2008-08-06
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0a.0 Communication controller: Agere Systems LT WinModem (rev 02)

---

### Post by overdrank on 2008-08-06
Hi and the intel graphics usually work well with ubuntu and compiz. How did you install the drivers? The drivers are installed with Ubuntu. If you have not tried to use the xfix option in recovery mode or just reconfigure your xorg. ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` If the desktop effect fail then you may look a compiz-check in the FAQ's
[http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

### Post by adamant715 on 2008-08-06
Compiz-Check hasnt helped me at all, this is the output of it.

>  Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
 Driver in use:         vesa
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: vesa driver in use 

All I want to know is how to switch to  a driver thats from Intel not Vesa.

---

### Post by overdrank on 2008-08-06
> **adamant715 said:**
> Compiz-Check hasnt helped me at all, this is the output of it.



All I want to know is how to switch to  a driver thats from Intel not Vesa.

Ok try the xfix option or the reconfigure I mentioned earlier post. Also I was searching your threads and found
[http://ubuntuforums.org/showthread.php?t=866561](http://ubuntuforums.org/showthread.php?t=866561)
Your system has
```
description: System memory
physical id: 0
size: 247MiB
```
so to me that means that 9mb is being shared with the intel graphics and I do not believe this will be enough for compiz.

---

### Post by adamant715 on 2008-08-06
Wow, that suck. :( Well this can be closed then.

---

### Post by dannyboy79 on 2008-08-06
well if you're using vesa, than compiz definitely won't work. what does this return

cat /etc/X11/xorg.conf | grep Driver

---

### Post by adamant715 on 2008-08-06
Driver		"kbd"
	Driver		"mouse"
	Driver		"vesa"

---

### Post by dannyboy79 on 2008-08-07
first backup your current xorg.conf file using this command

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_8-7-08
```

then open your xorg.conf file using this command

```
gksudo gedit /etc/X11/xorg.conf
```

once in gedit, change the Driver from "vesa" to "intel".

make sure you save before exiting gedit.  then to restart your xserver, hit these buttons at the same time, ctrl-alt-backspace. if your xserver doesn't restart and it errors out, then just log into a terminal session, and redit your xorg.conf file back to "vesa" instead of "intel" but that should work. good luck

---

### Post by adamant715 on 2008-08-07
Well I got it to work but the resoulutions huge.

---

### Post by dannyboy79 on 2008-08-07
what does your xorg.conf file have in it for resolutions? Also, can't you just change the resolution in the System, Preferences, Screen Resolution?

---

### Post by adamant715 on 2008-08-07
No, it says XServer does not support this or something.

And this is my xorg

> Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc101"
	Option		"XkbLayout"	"us "
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
	Option		"UseFBDev"		"true"
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
EndSection

---

### Post by dannyboy79 on 2008-08-07
your xorg.conf file is still using vesa, I thought you changed it to intel? Not to mention it's missing a whole bunch of stuff that's in almost all xorg.conf files I have seen. Here's an example but don't use it for your's.

# xorg.conf (xorg X Window System server configuration file)
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

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection


first back up your current xorg.conf file again then run this command.
```
sudo dpkg-reconfigure xserver-xorg
```
it will ask you a bunch of questions, most importantly which driver to use, pick intel. pick which resolutions you want, then for all other questions that you don't know just let the default stay the way it is. then restart your xserver again.

---

### Post by adamant715 on 2008-08-07
It doesnt ask about drivers though...=\ only keyboard

---

### Post by dannyboy79 on 2008-08-07
huh? I am not sure, if you're using Gutsy or Hardy then I am not sure. Sorry.

---

### Post by overdrank on 2008-08-07
> **adamant715 said:**
> It doesnt ask about drivers though...=\ only keyboard

Hi and have you tried to boot into recovery mode and use the xfix option?

---

### Post by adamant715 on 2008-08-07
I&#314;l try that

---

### Post by jimv on 2008-08-07
> **dannyboy79 said:**
> your xorg.conf file is still using vesa, I thought you changed it to intel? Not to mention it's missing a whole bunch of stuff that's in almost all xorg.conf files I have seen. Here's an example but don't use it for your's.

His xorg.conf is fine.  It looks like what default xorg.conf for Hardy should look like.  Your machine has a bunch of extra input devices that he doesn't have.

The problem is that his machine is defaulting to the VESA driver for a chipset that should be supported by the Intel i810 driver.  I suggest going into the BIOS and checking to see if there is a spot where you can allocate additional RAM to the graphics card.

---

### Post by adamant715 on 2008-08-13
I gave up, I just went back to XP but will try to dual boot.

---

