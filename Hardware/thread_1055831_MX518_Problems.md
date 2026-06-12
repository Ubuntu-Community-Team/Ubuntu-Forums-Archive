---
title: "MX518 Problems"
date: 2009-01-31
forum: Hardware
---

### Post by MetalFanLiam on 2009-01-31
Im having a problem with the Logitech MX518 optical mouse. The side buttons, and the buttons on top do not work during gameplay of Wolfenstein enemy territory. I have searched around and tried a few different approaches such as imwheel, and editting the xorg config to show this:

Section "InputDevice"
        Identifier    "Configured Mouse"
        Driver        "mouse"
    Option        "Protocol"        "evdev"
    Option        "Dev Name"        "Logitech USB-PS/2 Optical Mouse"
    Option        "Dev Phys"        "usb-0000:00:13.0-1/input0"
        Option        "Device"      "/dev/input/event2"  
    Option        "Buttons"        "10"
    Option        "ZAxisMapping"        "4 5"
EndSection

After restarting X, the problem still remained and a solution is yet to be found. My system spec is:

CPU INFORMATION
	GenuineIntel, Intel(R) Core(TM)2 CPU          6420  @ 2.13GHz
	Number of CPUs: 1
	CPU clock currently at 2133.392 MHz with 4096 KB cache
	Numbering: family(6) model(15) stepping(6)
	Bogomips: 4266.78
	Flags: fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm

MEMORY INFORMATION
	Total memory: 3038 MB
	Total swap: 953 MB

STORAGE INFORMATION
	SCSI device -  scsi0
		Vendor:  ATA      
		Model:  Hitachi HDT72503 
	SCSI device -  scsi1
		Vendor:  ATA      
		Model:  ST3250820AS      
	SCSI device -  scsi4
		Vendor:  Optiarc  
		Model:  DVD RW AD-5170A  
	SCSI device -  scsi6
		Vendor:  Generic  
		Model:  USB SD Reader    

HARDWARE INFORMATION
MOTHERBOARD
	Host bridge
		ATI Technologies Inc Radeon Xpress 7930 Host Bridge
		Subsystem: Micro-Star International Co., Ltd. Device 7326
	PCI bridge(s)
		ATI Technologies Inc RS7933 PCI Bridge
		ATI Technologies Inc RS7936 PCI Bridge
		ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
		ATI Technologies Inc RS7933 PCI Bridge
		ATI Technologies Inc RS7936 PCI Bridge
		ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
	USB controller(s)
		ATI Technologies Inc SB600 USB (OHCI0) (prog-if 10)
		ATI Technologies Inc SB600 USB (OHCI1) (prog-if 10)
		ATI Technologies Inc SB600 USB (OHCI2) (prog-if 10)
		ATI Technologies Inc SB600 USB (OHCI3) (prog-if 10)
		ATI Technologies Inc SB600 USB (OHCI4) (prog-if 10)
		ATI Technologies Inc SB600 USB Controller (EHCI) (prog-if 20)
		ATI Technologies Inc SB600 USB (OHCI0) (prog-if 10)
		ATI Technologies Inc SB600 USB (OHCI1) (prog-if 10)
		ATI Technologies Inc SB600 USB (OHCI2) (prog-if 10)
		ATI Technologies Inc SB600 USB (OHCI3) (prog-if 10)
		ATI Technologies Inc SB600 USB (OHCI4) (prog-if 10)
		ATI Technologies Inc SB600 USB Controller (EHCI) (prog-if 20)
	ISA bridge
		ATI Technologies Inc SB600 PCI to LPC Bridge
		Subsystem: Micro-Star International Co., Ltd. Device 7326
	IDE interface
		ATI Technologies Inc SB600 IDE (prog-if 8a [Master SecP PriP])
		Subsystem: Micro-Star International Co., Ltd. Device 7326

GRAPHIC CARD
	VGA controller
		nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
		Subsystem: Giga-byte Technology Device 3417

SOUND CARD
	Multimedia controller
		ATI Technologies Inc SBx00 Azalia (Intel HDA)
		Subsystem: Micro-Star International Co., Ltd. Device 7326

NETWORK
	Ethernet controller
		Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
		Subsystem: Micro-Star International Co., Ltd. Device 326c

NVIDIA GRAPHIC CARD INFORMATION
	Model name: GeForce 7600 GT
	Card Type: PCI-E 16x
	Video RAM: 256 MB
	GPU Frequency: 560 MHz
	Driver version: NVIDIA UNIX x86 Kernel Module  177.82  Tue Nov  4 13:35:57 PST 2008

Thanks for the help,
MFL

---

### Post by Yashiro on 2009-01-31
**The following will not work on Ubuntu 8.10 or above.**

1) Install lomoco, btnx, xmodmap.
> sudo apt-get lomoco btnx xmodmap btnx-config

2) Make a new file in your home dir called **.Xmodmap**
Put this into it. 
> pointer = 1 2 3 4 5 6 7 10 9 8

3) Goto System menu, Preferences, Sessions
Add a new process here to run at startup. The command is
> xmodmap ~/.xmodmap

4) Edit **/etc/rc.local** and add this to the bottom
> lomoco --pid=c01e -m --no-sms
exit 0

5) **Xorg.conf should look like this:**
> Section "InputDevice"
	Identifier  "MX518 Optical Mouse"
	Driver      "evdev"
	Option	    "Name" "Logitech USB-PS/2 Optical Mouse"
	Option	    "AllowMouseOpenFail" "true"
	Option	    "VertScrollDelta" "12"
	Option	    "Resolution" "1200"
	Option	    "Emulate3Buttons" "false"
EndSection

6) Reboot and run **btnx**.
You should be able to assign all your buttons apart from the 'task switcher'. I have the following keycodes set.

Small button above the mouse wheel - Button 8 - KEY_PAGEUP
Small button to the rear of the mouse wheel - Button 7 - KEY_PAGEDOWN
Thumb button "Back" Button 4 - KEY_RIGHT,modifier of KEY_LEFTALT
Thumb button "Forward" Button 5 - KEY_LEFT,modifier of KEY_LEFTALT

Back, forward work in browsers and nautilus.
Never had a problem binding keys in any id games.

And, yes, this was a not fun to work out. Please fix button recognition in Ubuntu.

---

### Post by MetalFanLiam on 2009-01-31
Thanks, but is there a fix for 8.10? AS this is what i am currently running.

---

### Post by Yashiro on 2009-01-31
You'd have to test various steps but I doubt it.
Btnx does not work properly in 8.10. Look in the huge mouse thread for fixes.

---

