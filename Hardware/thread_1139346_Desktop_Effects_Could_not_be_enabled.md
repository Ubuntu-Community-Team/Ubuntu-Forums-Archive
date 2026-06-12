---
title: "Desktop Effects Could not be enabled"
date: 2009-04-26
forum: Hardware
---

### Post by legendaryred on 2009-04-26
Hi all, 
I just installed Ubuntu 9.04 and everything is working fine. Except when i try to enable Desktop Effects a pop up appears saying "searching for drivers" then the screen starts to blink as if it were to work, but in the end it says "desktop effects could not be enabled". I am running an Intel 82865G Integrated Graphics. I been looking for a solution such as installing xserver-xgl. However, everytime I run the command 

apt-get *install xserver*-[I]xgl
[/I]
I get this error: 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xserver-xgl

I hope somebody could help me. 
By the way this is my graphics card 

[I]00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:01.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
[/I]
Hope somebody can help me. 
Thanks in advance!

---

### Post by SpitfireSMS on 2009-04-27
For desktop effects to be enabled you need a driver for your graphics chipset.
Go to System>Administration>Hardware Drivers
I dont have an intel chipset, so im not sure exactly what you'll see.
But if you do see a driver, then go ahead and enable it, restart, and it should all be good:P

---

### Post by gymophett on 2009-04-27
I found a real easy fix. It happens with intel cards.
Go to the terminal, and copy and paste the code below.

```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

And you have effects now! :D

---

### Post by legendaryred on 2009-04-27
> **SpitfireSMS said:**
> For desktop effects to be enabled you need a driver for your graphics chipset.
Go to System>Administration>Hardware Drivers
I dont have an intel chipset, so im not sure exactly what you'll see.
But if you do see a driver, then go ahead and enable it, restart, and it should all be good:P
I tried that and it says" No propietrary drivers could be found" and everything else is just empty.

---

### Post by legendaryred on 2009-04-27
> **gymophett said:**
> I found a real easy fix. It happens with intel cards.
Go to the terminal, and copy and paste the code below.

```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```And you have effects now! :D
I tried it and it sends me this:
[I]
seoane@seoane-desktop:~$ mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
seoane@seoane-desktop:~$ seoane
bash: seoane: command not found
[/I]
Did i do something wrong?

---

### Post by gymophett on 2009-04-27
> **legendaryred said:**
> I tried it and it sends me this:
[I]
seoane@seoane-desktop:~$ mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
seoane@seoane-desktop:~$ seoane
bash: seoane: command not found
[/I]
Did i do something wrong?

No, you entered seoane after the code for some reason, and seoane is your computer name, not a command.

Let me try again.

Paste the code I gave you in your terminal and press enter.
Then exit the terminal.
Right click your desktop and click 'Change desktop background'.
Click 'visual effects'
Then click Normal or Extra, and it should work.
:)

---

### Post by legendaryred on 2009-04-27
> **gymophett said:**
> No, you entered seoane after the code for some reason, and seoane is your computer name, not a command.

Let me try again.

Paste the code I gave you in your terminal and press enter.
Then exit the terminal.
Right click your desktop and click 'Change desktop background'.
Click 'visual effects'
Then click Normal or Extra, and it should work.
:)
I'm sorry about that. 
Ok i did what you said and when i click "normal" the whole desktop went white and i could only see my cursor. After like 15 seconds it returns to normal with "none" selected. It didn't send an error of some kind. I think this has to do something with my graphics chip. Any ideas?

---

### Post by gymophett on 2009-04-27
> **legendaryred said:**
> I'm sorry about that. 
Ok i did what you said and when i click "normal" the whole desktop went white and i could only see my cursor. After like 15 seconds it returns to normal with "none" selected. It didn't send an error of some kind. I think this has to do something with my graphics chip. Any ideas?

Interesting. I'm new to Linux, so I might not be the best help, but I'll try as best as I can.
Maybe all of the correct drivers aren't installed?

Lets revert your driver back to 2.4 and it should work. :)

Here we go:

Add the following lines to your /etc/apt/sources.list: 
To get there:
Go to Places>Home folder>File System>etc>apt
When you are there, right click sources.list and open with text editor.
Then copy and paste the lines below and save it.

```

 deb http://ppa.launchpad.net/siretart/ppa/ubuntu jaunty main
 deb-src http://ppa.launchpad.net/siretart/ppa/ubuntu jaunty main
```

Install the driver: 
```

sudo apt-get update
sudo apt-get install xserver-xorg-video-intel-2.4

```

Now you should be set. Restart X and see if the graphics performance from intrepid is restored.

---

### Post by legendaryred on 2009-04-27
> **gymophett said:**
> Interesting. I'm new to Linux, so I might not be the best help, but I'll try as best as I can.
Maybe all of the correct drivers aren't installed?

Lets revert your driver back to 2.4 and it should work. :)

Here we go:

Add the following lines to your /etc/apt/sources.list: 
To get there:
Go to Places>Home folder>File System>etc>apt
When you are there, right click sources.list and open with text editor.
Then copy and paste the lines below and save it.

```

 deb http://ppa.launchpad.net/siretart/ppa/ubuntu jaunty main
 deb-src http://ppa.launchpad.net/siretart/ppa/ubuntu jaunty main
```Install the driver: 
```

sudo apt-get update
sudo apt-get install xserver-xorg-video-intel-2.4

```Now you should be set. Restart X and see if the graphics performance from intrepid is restored.
Wow, It worked!
Thanks a lot for your help. I was getting frustrated with this. It worked magnificently.
Hope this helps other people!
Thanks again!:popcorn:

---

### Post by gymophett on 2009-04-27
> **legendaryred said:**
> Wow, It worked!
Thanks a lot for your help. I was getting frustrated with this. It worked magnificently.
Hope this helps other people!
Thanks again!:popcorn:

You're very welcome! Any time.:P

---

### Post by Talsinc on 2009-04-27
> **gymophett said:**
> I found a real easy fix. It happens with intel cards.
Go to the terminal, and copy and paste the code below.

```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```And you have effects now! :D


Worked like a charm!  Thanks!

---

### Post by echo47 on 2009-04-27
This worked for me as well, thank you very much!

---

### Post by bhashadi on 2009-04-28
> **gymophett said:**
> I found a real easy fix. It happens with intel cards.
Go to the terminal, and copy and paste the code below.

```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

And you have effects now! :D

Worked perfectly for me too... I am on an Acer Aspire 5920 laptop with following lspci output

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
0a:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
0a:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0a:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
0a:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
0a:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

Many thanks to gymophett

---

### Post by aksival on 2009-04-29
> **gymophett said:**
> I found a real easy fix. It happens with intel cards.
Go to the terminal, and copy and paste the code below.

```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

And you have effects now! :D

Thanks, Gavin.  Works like a charm :D

I have noticed an issue with dual screens, though.  The second monitor flakes out and only displays properly on the left 1/8th of the screen.  The rest of it is just noise.

Also, anyone have any ideas why I'm not seeing any restricted drivers available?  I just ran an upgrade from 8.x --> 9.04 yesterday and before I was using the ATI restricted drivers (plus effects) with no problems.

Not a big deal, of course, but the effects do make the desktop that much better :)

---

### Post by kehon on 2009-04-30
thanks very much this command also worked for me man been trying to get this for days i love those effects so much better for the eye and it wraps around the workspaces 

```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

---

### Post by octrin19 on 2009-04-30
Yes, it worked for me, too. THANKS!!

---

### Post by johnjust on 2009-05-05
Hello all, I'm having this exact same problem, except I don't have an Intel graphics card.  It's an NVIDIA GeForce G 105M 256MB on a Lenovo Thinkpad SL500 (which is known to have issues with Ubuntu).

When I installed Jaunty, "Hardware Drivers" told em to install Nvidia driver 180, which I did, and it says it's activated.  But, I cannot enable effects, my max resolution isn't listed, and when I open the "Display" dialog, it lists my laptop monitor as "Unrecognizable".  I'm on a work PC now, but if you need and output, I brought it with me - just let me know.

Thanks for any help.

---

### Post by lakshm on 2009-05-05
> **gymophett said:**
> Interesting. I'm new to Linux, so I might not be the best help, but I'll try as best as I can.
Maybe all of the correct drivers aren't installed?

Lets revert your driver back to 2.4 and it should work. :)

Here we go:

Add the following lines to your /etc/apt/sources.list: 
To get there:
Go to Places>Home folder>File System>etc>apt
When you are there, right click sources.list and open with text editor.
Then copy and paste the lines below and save it.

```

 deb http://ppa.launchpad.net/siretart/ppa/ubuntu jaunty main
 deb-src http://ppa.launchpad.net/siretart/ppa/ubuntu jaunty main
```Install the driver: 
```

sudo apt-get update
sudo apt-get install xserver-xorg-video-intel-2.4

```Now you should be set. Restart X and see if the graphics performance from intrepid is restored.
wow thanks........ desktop effects working like charm.......:-({|=

---

### Post by drubdrub on 2009-05-06
This did not work for me.  Thanks, anyway.

> **gymophett said:**
> I found a real easy fix. It happens with intel cards.
Go to the terminal, and copy and paste the code below.

```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

And you have effects now! :D

---

### Post by spaided on 2009-05-06
> **gymophett said:**
> i found a real easy fix. It happens with intel cards.
Go to the terminal, and copy and paste the code below.

```
mkdir -p ~/.config/compiz/ && echo skip_checks=yes >> ~/.config/compiz/compiz-manager
```

and you have effects now! :d
omg thanks a million!!!!!!!!

---

### Post by Turtleman on 2009-05-07
> **gymophett said:**
> Interesting. I'm new to Linux, so I might not be the best help, but I'll try as best as I can.
Maybe all of the correct drivers aren't installed?

Lets revert your driver back to 2.4 and it should work. :)

Here we go:

Add the following lines to your /etc/apt/sources.list: 
To get there:
Go to Places>Home folder>File System>etc>apt
When you are there, right click sources.list and open with text editor.
Then copy and paste the lines below and save it.

```

 deb http://ppa.launchpad.net/siretart/ppa/ubuntu jaunty main
 deb-src http://ppa.launchpad.net/siretart/ppa/ubuntu jaunty main
```

Install the driver: 
```

sudo apt-get update
sudo apt-get install xserver-xorg-video-intel-2.4

```

Now you should be set. Restart X and see if the graphics performance from intrepid is restored.

I am having the same problem. I tried doing what you said, but when I try to save resources.list it says I don't have permission to. What should I do then?

---

### Post by Vikhyath on 2009-05-11
> Ok i did what you said and when i click "normal" the whole desktop went white and i could only see my cursor. After like 15 seconds it returns to normal with "none" selected. It didn't send an error of some kind. I think this has to do something with my graphics chip. Any ideas?


I still keep gettin that!... help:confused:

---

### Post by zqzh on 2009-05-12
> **gymophett said:**
> I found a real easy fix. It happens with intel cards.
Go to the terminal, and copy and paste the code below.

```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

And you have effects now! :D
It really works.
Thanks:)

---

### Post by Walter Melon on 2009-05-13
Can anyone help me?  I have the same problem but instead of an Intel card, I have an nVIDIA geforce 9300M GS.

---

### Post by Walter Melon on 2009-05-13
here's the Xorg.0.log

```
X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux aalok-laptop 2.6.28-12-generic #43-Ubuntu SMP Fri May 1 19:27:06 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed May 13 11:34:22 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) nVidia Corporation GeForce 9300M GS rev 161, Mem @ 0xce000000/16777216, 0xd0000000/268435456, 0xcc000000/33554432, I/O @ 0x00002000/128
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "freetype"
(WW) Warning, couldn't open module freetype
(II) UnloadModule: "freetype"
(EE) Failed to load module "freetype" (module does not exist, 0)
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  180.44  Mon Mar 23 15:29:02 PST 2009
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  180.44  Mon Mar 23 15:05:32 PST 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 9300M GS (G98) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 62.98.43.00.08
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 9300M GS at PCI:1:0:0:
(--) NVIDIA(0):     Seiko (DFP-0)
(--) NVIDIA(0): Seiko (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): Seiko (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1366 x 768
(--) NVIDIA(0): DPI set to (99, 97); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): ACPI display change hotkey events enabled: the X server is new
(II) NVIDIA(0):     enough to receive ACPI display change hotkey events.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event5"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Video Bus: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Video Bus: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) Video Bus: xkb_layout: "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.99.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 0.99.3
(**) Option "Device" "/dev/input/event7"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle double triple
(--) SynPS/2 Synaptics TouchPad touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) filter chain progression: 2.00
(**) SynPS/2 Synaptics TouchPad: (accel) filter stage 0: 20.00 ms
(**) SynPS/2 Synaptics TouchPad: (accel) set acceleration profile 0
(--) SynPS/2 Synaptics TouchPad touchpad found
```

---

### Post by Dotsona on 2009-05-15
I was curious if anyone has addressed the dual screen rendering issues, I have now enabled desktop effects, however now I am getting some rendering issues on the 2nd display

[http://img191.imageshack.us/img191/8664/screenshot.png](http://img191.imageshack.us/img191/8664/screenshot.png)

(note this only occurs when I bump the resolution above 1040)

---

### Post by iamleaf on 2009-05-20
I have the same problem. I don't know what graphics card I have, I just know that its Intel. And I've tried all of the above... but it still has not worked. All that shows up when I click the 'normal' option in the Visual Effects tab is my wallpaper and my cursor, the keyboard commands don't work, the mouse clicks don't work. Someone please help? I've also tried rolling back the driver but I don't even know if I did it correctly because it still doesn't work.

---

### Post by nickk9 on 2009-05-27
I think it was changing to the intel2.4 driver that worked for me in the end (Intel 82865G), i tried so many suggestions from around the web i'm not sure what really fixed it because this page:

[http://phillapier.com/?p=188](http://phillapier.com/?p=188)

reminded me i had enabled gnome's compositing feature (i'm using linux mint 7 - this is accessed from mintdesktop application). Disabling that solved my problem.

thanks to all here!

---

### Post by Razmear on 2009-05-28
The command > mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager fixed the issue for me using Nvidia GE 9200 and the version 180 drivers using dual screens. 

Thanks!!!
eb

---

### Post by ontadimanamana on 2009-06-01
yeah
i love it :D desktop effect enabled
thank you

---

### Post by nilufer on 2009-08-17
```

 deb http://ppa.launchpad.net/siretart/ppa/ubuntu jaunty main
 deb-src http://ppa.launchpad.net/siretart/ppa/ubuntu jaunty main
```

Install the driver: 
```

sudo apt-get update
sudo apt-get install xserver-xorg-video-intel-2.4

```

I was also totally disappointed with the effects being vanished with the new version, I was not able to use my dock avant-window-navigator.

This fix really worked.
I used to update the packages daily looking for this to be fixed but there wasn't a fix so far.

Thanks a lot for the fix Turtleman.
Nilufer

---

### Post by nilufer on 2009-08-17
> **iamleaf said:**
> I have the same problem. I don't know what graphics card I have, I just know that its Intel. And I've tried all of the above... but it still has not worked. All that shows up when I click the 'normal' option in the Visual Effects tab is my wallpaper and my cursor, the keyboard commands don't work, the mouse clicks don't work. Someone please help? I've also tried rolling back the driver but I don't even know if I did it correctly because it still doesn't work.

Rolling back the driver actually worked for me.
After rolling back, initially I tried to change the effects from "None" to "Normal".
It did not work actually.(could not be enabled message appeared)
Then i tried to change from "None" to "Extra".
That worked and after then i switched to "Normal".
Now it works perfectlry.

This may sound odd, but believe me thats how it worked for me.

---

### Post by Bhanu Pratap Singh on 2009-10-14
> **gymophett said:**
> Interesting. I'm new to Linux, so I might not be the best help, but I'll try as best as I can.
Maybe all of the correct drivers aren't installed?

Lets revert your driver back to 2.4 and it should work. :)

Here we go:

Add the following lines to your /etc/apt/sources.list: 
To get there:
Go to Places>Home folder>File System>etc>apt
When you are there, right click sources.list and open with text editor.
Then copy and paste the lines below and save it.

```

 deb http://ppa.launchpad.net/siretart/ppa/ubuntu jaunty main
 deb-src http://ppa.launchpad.net/siretart/ppa/ubuntu jaunty main
```Install the driver: 
```

sudo apt-get update
sudo apt-get install xserver-xorg-video-intel-2.4

```Now you should be set. Restart X and see if the graphics performance from intrepid is restored.


hi, the code you gave is not copying in the file sources.list. It is a read only file. Can you suggest me any way how to manipulate the file?
I really need the answer...
My computer is an older version computer having intel pentium 4 processor. Can desktop effects not be enabled in that?
Waiting an answer......

---

### Post by Langleyo on 2009-10-25
This worked for me on my Toshiba Satellite A100 332 laptop but only after all icons disappeared and not allowing any keyboard or mouse input at all. I rebooted, right clicked on desktop background, change desktop background - visual effects - extra, and its now up and running, though I'm baffled as to why it stopped in the first place (I turned off effects to run Google Earth as I've done thousands of times). Saying that though, I did patch in a new libGL.so.1.2 file to get rid of the stupid slow running of the atmosphere effects. Wonder if that broke it? Ooops.


Thanks, grateful Ubuntu Jaunty user Langleyo

---

