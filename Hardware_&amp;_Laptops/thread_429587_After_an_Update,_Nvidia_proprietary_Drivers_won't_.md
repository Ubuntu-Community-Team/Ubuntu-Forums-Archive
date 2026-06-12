---
title: "After an Update, Nvidia proprietary Drivers won't work with the new Kernel"
date: 2007-05-01
forum: Hardware &amp; Laptops
---

### Post by darkmaster on 2007-05-01
First of all, I'm running right now on Ubuntu Edgy and have an Nvidia Ge Force GO7600 card on my laptop.
A few months ago I updated and a new Kernel version was available. This version appeared in Grub as the first one (Since it is new). 
If I try to boot with this version, (.14 I guess? It doesn't matter much, continue reading) at a certain point Ubuntu halts and the ugly blue-gray screen appears telling me that X couldn't start. Details and it tells me it cannot find the Nvidia card.
So I thought I had to reinstall the driver but I noticed that if I boot the old Kernel, the Nvidia card works just fine! I downloaded Envy since I'm not able to manually install the driver. Then I rebooted with the new kernel in recoery mode and installed the driver using Envy. All good. Reboot and... tadan! Nothing changes. Still unable to load X and still the same error. 

Some days ago I backuped and upgraded to feisty. Of course, now the Kernel is even newer than before (Something like .20 I guess). Same problem, tryed to reinstall the driver with the new envy for feisty, nothing changes. And after upgrading, if I try to boot with the old kernel that worked it does not work anymore! Ah! That's really funny if it wasn't tragic.

What's the deal? I had to run the open source ugly without 3D driver for some days, hoping things would have been fixed but... after some days I changed back to my backuped version of edgy, from wich I'm wrighting right now. Any hope to have my damned Nvidia driver working with the new kernels? And why is it giving me all these problems?

---

### Post by darkmaster on 2007-05-03
Hey boys, nobody willing to help? I can't believe I'm the only one having this problem here...

---

### Post by tseliot on 2007-05-03
let's try to diagnose the error:

Boot with the "nv" driver in your xorg.conf

Then (after Ubuntu has booted) Set the driver to "nvidia" in your /etc/X11/xorg.conf
Log out and Press CTRL+ALT+F1

You will get to the command line (no GUI)
Type:

```
sudo /etc/init.d/gdm stop (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm stop (if you use KDM)
```

Then:
```
startx -- -verbose 5 -logverbose 5
```

You will see several lines with the same error.

Then if you can't get to the command line press CTRL+ALT+F1 or CTRL+C (select NO if it asks you if you want to see the output of the error or something like that)

Then type this in order to copy the output of the error to your home folder:
```
sudo cp /var/log/Xorg.0.log /home/your_username/Xorg.0.log
```
(Of course you have to replace "your_username" with your username)

Access the GNOME or KDE again in the following way:
```
sudo nano /etc/X11/xorg.conf
```
Set the driver back to "nv" instead of "nvidia"
CTRL+O to save
CTRL+X to exit

Then
```
sudo /etc/init.d/gdm restart (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm restart (if you use KDM)
```


Post the content of that file (which you can find under /home/your_username/Xorg.0.log )

---

### Post by darkmaster on 2007-05-03
Hi, thanks for the very quick answer :)
i'm working now from my Mac G5, and am following yor indications on the Linux PC. Aniway, I use Ubuntu Edgy, Gnome. i'll tell you in a few minutes the answer, stay tuned :)

---

### Post by darkmaster on 2007-05-03
Ehm.. I lost my backuped Feisty.... sorry. I'll have to backup the working Edgy and Upgrade to feisty again. So this is going to stay freezed for some hours... I gues... :(
Well, that's allready good that you're helping me :) Catch you soon :)

---

### Post by darkmaster on 2007-05-04
Very well, so I upgraded to Feisty. Now I have a very well know network problem, it freezes Ubuntu at startup as in this topip: 

But that's another story and I think I found out how to work it around reading the link in the post. I'll try it but that OT from this post. 

I changed as you say in your faq to nv driver and restarted before the upgrade. All was good and after restart the new nuveau (Or something like that) driver setted a very nice resolution but no 3D, of course. Here comes the weird news. I tryed out restricted drivers manager. It warned me I had to use the restricted Nvidia driver. I activated it, restarted, and hey! In Zorg there's nvidia but I have no 3D. No 3D application starts but: no 3D application works at all!

example: screensavers won't even show themselves if they are 3D accelerated. Trying to launch Billard GL I get this outpoot:

```
billard-gl

 BillardGL (C) 2001, 2002 Tobias Nopper, Stefan Disch, Martina Welte

freeglut (billard-gl): OpenGL GLX extension not supported by display ':0.0'
```

Or trying to launch accelerator3D:
```

accelerator3d
Could not set screen mode
```

And so on with any other 3D application, even Beryl automatically crashes and falls back to Metacity. Desktop Effects cannot be activated and so on and on and on. You got a scenary I guess.

So, now I'm in a moment I need 3D. How do I make it work? I think I'll have to use your Envy... the program I mean :) But how? Do I have to disable the restricted Nvidia driver in use before it? Should I better add to my repos your other project to keep up-to-date the 3D drivers? What would you do in my position? 

Thanks a lot for your help :)

---

### Post by darkmaster on 2007-05-05
Thanks aniway but after one single try everything went well. Dunno why it didn't before. The steps I did, in order:

1) Unable Nvidia proprietary driver from driver manager.
2) Restart
3) Log-in with nv driver, download Envy, install it.
4) Reboot and at log-in quit with ctrl + f1
5) Log in the textual interface and gdm stop
6) Run envy -t and uninstalled nvidia driver
7) Run evny -t and install Nvidia driver.
8) At reboot nvidia worked great!

That's strange I think the problem was that I used envy in the recovery mode... there's no other explanation. Or maybe envy's Nvidia driver conflicted with Ubuntu's one... I really don't know.

Sorry for bothering you but now it works and thatnks aniway for trying to help me out.
Now the problem is at login, GNOME freezes damn it... and it's not a network manager issue.

[http://ubuntuforums.org/showthread.php?p=2590051](http://ubuntuforums.org/showthread.php?p=2590051)

Bye!

---

### Post by darkmaster on 2007-05-07
All good things has to end someday... in my case, good things ended very soon, dammit.
On the last update I had from Trevino's repository, I received a new Kernel wich wasintended to have some new freeze and suspend feature, or that's what I understood... the kernel is 2.6.20-15-generic.

After installing this and rebooting, I had no Nvidia driver. So I booted with nv thinking it was not such a problem, logged out, launched envy, uninstalled the Nvidia driver, reinstalled it and nothing changed. X didn't boot. So I rebooted with nv, purged Envy, reinstalled it, exited and reinstalled the nvidia driver and still nothing.,... at this point I really don't know what to do. One thing is certain: this Nvidia driver is really problematic to handle!! 

Evry update messes things up! Guess that if I solve this I'll stay with my kernel for a very long time. I followed your instructions and here's is the xorg outpoot. Can you help me please ? :( Sorry for othering you again.... :_(


> X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux localhost 2.6.20-15-generic #1 SMP Mon Apr 23 06:12:00 CEST 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon May  7 11:56:48 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA Corporation NVIDIA Default Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Option "AIGLX" "true"
(**) Extension "Composite" is enabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,02f7 card 1043,1367 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,02fa card 1043,1367 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,02fe card 1043,1367 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,02f8 card 1043,1367 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:4: chip 10de,02f9 card 1043,1367 rev a2 class 05,00,00 hdr 00
(II) PCI: 00:00:5: chip 10de,02ff card 1043,1367 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:6: chip 10de,027f card 1043,1367 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:7: chip 10de,027e card 1043,1367 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:03:0: chip 10de,02fd card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:04:0: chip 10de,02fb card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10de,0270 card 1043,1367 rev a2 class 05,00,00 hdr 00
(II) PCI: 00:0a:0: chip 10de,0260 card 1043,1367 rev a3 class 06,01,00 hdr 80
(II) PCI: 00:0a:1: chip 10de,0264 card 1043,1367 rev a3 class 0c,05,00 hdr 80
(II) PCI: 00:0a:3: chip 10de,0271 card 1043,1367 rev a3 class 0b,40,00 hdr 80
(II) PCI: 00:0b:0: chip 10de,026d card 1043,1367 rev a3 class 0c,03,10 hdr 80
(II) PCI: 00:0b:1: chip 10de,026e card 1043,1367 rev a3 class 0c,03,20 hdr 80
(II) PCI: 00:0d:0: chip 10de,0265 card 1043,1367 rev a1 class 01,01,8a hdr 00
(II) PCI: 00:10:0: chip 10de,026f card 0000,0000 rev a2 class 06,04,01 hdr 81
(II) PCI: 00:10:1: chip 10de,026c card 1043,1367 rev a2 class 04,03,00 hdr 80
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10ec,8168 card 1043,11f5 rev 01 class 02,00,00 hdr 00
(II) PCI: 02:00:0: chip 10de,0398 card 1043,1322 rev a1 class 03,00,00 hdr 00
(II) PCI: 03:01:0: chip 1180,0476 card e000,0000 rev b3 class 06,07,00 hdr 82
(II) PCI: 03:01:1: chip 1180,0552 card 1043,1367 rev 08 class 0c,00,10 hdr 80
(II) PCI: 03:01:2: chip 1180,0822 card 1043,1367 rev 17 class 08,05,00 hdr 80
(II) PCI: 03:01:3: chip 1180,0592 card 1043,1367 rev 08 class 08,80,00 hdr 80
(II) PCI: 03:03:0: chip 14e4,4318 card 1043,120f rev 02 class 02,80,00 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:3:0), (0,1,1), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdcf00000 - 0xdcffffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:4:0), (0,2,2), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xdd000000 - 0xdf6fffff (0x2700000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:10:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:16:0), (0,3,7), BCTRL: 0x0202 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xdf700000 - 0xdfffffff (0x900000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xda000000 - 0xdbffffff (0x2000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-CardBus bridge:
(II) Bus 4: bridge is at (3:1:0), (3,4,7), BCTRL: 0x0583 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[1] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
(--) PCI: (0:10:3) nVidia Corporation MCP51 PMU rev 163, Mem @ 0xdcec0000/18
(--) PCI:*(2:0:0) nVidia Corporation G70 [GeForce Go 7600] rev 161, Mem @ 0xde000000/24, 0xc0000000/28, 0xdd000000/24, I/O @ 0xdc00/7, BIOS @ 0xdf6e0000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xdf7fc000 - 0xdf7fdfff (0x2000) MX[B]
	[1] -1	0	0xdf7ffc00 - 0xdf7ffcff (0x100) MX[B]
	[2] -1	0	0xdf7ff800 - 0xdf7ff8ff (0x100) MX[B]
	[3] -1	0	0xdf7ff000 - 0xdf7ff7ff (0x800) MX[B]
	[4] -1	0	0xdcfff000 - 0xdcffffff (0x1000) MX[B]
	[5] -1	0	0xdceb8000 - 0xdcebbfff (0x4000) MX[B]
	[6] -1	0	0xdcebfc00 - 0xdcebfcff (0x100) MX[B]
	[7] -1	0	0xdcebe000 - 0xdcebefff (0x1000) MX[B]
	[8] -1	0	0xdf6e0000 - 0xdf6fffff (0x20000) MX[B](B)
	[9] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[12] -1	0	0xdcec0000 - 0xdcefffff (0x40000) MX[B]
	[13] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[14] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[15] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[16] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdf7fc000 - 0xdf7fdfff (0x2000) MX[B]
	[1] -1	0	0xdf7ffc00 - 0xdf7ffcff (0x100) MX[B]
	[2] -1	0	0xdf7ff800 - 0xdf7ff8ff (0x100) MX[B]
	[3] -1	0	0xdf7ff000 - 0xdf7ff7ff (0x800) MX[B]
	[4] -1	0	0xdcfff000 - 0xdcffffff (0x1000) MX[B]
	[5] -1	0	0xdceb8000 - 0xdcebbfff (0x4000) MX[B]
	[6] -1	0	0xdcebfc00 - 0xdcebfcff (0x100) MX[B]
	[7] -1	0	0xdcebe000 - 0xdcebefff (0x1000) MX[B]
	[8] -1	0	0xdf6e0000 - 0xdf6fffff (0x20000) MX[B](B)
	[9] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[12] -1	0	0xdcec0000 - 0xdcefffff (0x40000) MX[B]
	[13] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[14] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[15] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[16] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdf7fc000 - 0xdf7fdfff (0x2000) MX[B]
	[5] -1	0	0xdf7ffc00 - 0xdf7ffcff (0x100) MX[B]
	[6] -1	0	0xdf7ff800 - 0xdf7ff8ff (0x100) MX[B]
	[7] -1	0	0xdf7ff000 - 0xdf7ff7ff (0x800) MX[B]
	[8] -1	0	0xdcfff000 - 0xdcffffff (0x1000) MX[B]
	[9] -1	0	0xdceb8000 - 0xdcebbfff (0x4000) MX[B]
	[10] -1	0	0xdcebfc00 - 0xdcebfcff (0x100) MX[B]
	[11] -1	0	0xdcebe000 - 0xdcebefff (0x1000) MX[B]
	[12] -1	0	0xdf6e0000 - 0xdf6fffff (0x20000) MX[B](B)
	[13] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[16] -1	0	0xdcec0000 - 0xdcefffff (0x40000) MX[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[20] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[21] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[22] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
	[23] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B](B)
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9755
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules//fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9755
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) NVIDIA dlloader X Driver  1.0-9755  Mon Feb 26 23:23:13 PST 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 02:00:0
(WW) NVIDIA: No matching Device section for instance (BusID PCI:0:10:3) found
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) NVIDIA(0): Found 1 NVIDIA X Screens
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="NVIDIA Corporation"
	compiled for 7.1.99.2, module version = 1.0.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdf7fc000 - 0xdf7fdfff (0x2000) MX[B]
	[5] -1	0	0xdf7ffc00 - 0xdf7ffcff (0x100) MX[B]
	[6] -1	0	0xdf7ff800 - 0xdf7ff8ff (0x100) MX[B]
	[7] -1	0	0xdf7ff000 - 0xdf7ff7ff (0x800) MX[B]
	[8] -1	0	0xdcfff000 - 0xdcffffff (0x1000) MX[B]
	[9] -1	0	0xdceb8000 - 0xdcebbfff (0x4000) MX[B]
	[10] -1	0	0xdcebfc00 - 0xdcebfcff (0x100) MX[B]
	[11] -1	0	0xdcebe000 - 0xdcebefff (0x1000) MX[B]
	[12] -1	0	0xdf6e0000 - 0xdf6fffff (0x20000) MX[B](B)
	[13] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[16] -1	0	0xdcec0000 - 0xdcefffff (0x40000) MX[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[20] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[21] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[22] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
	[23] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdf7fc000 - 0xdf7fdfff (0x2000) MX[B]
	[5] -1	0	0xdf7ffc00 - 0xdf7ffcff (0x100) MX[B]
	[6] -1	0	0xdf7ff800 - 0xdf7ff8ff (0x100) MX[B]
	[7] -1	0	0xdf7ff000 - 0xdf7ff7ff (0x800) MX[B]
	[8] -1	0	0xdcfff000 - 0xdcffffff (0x1000) MX[B]
	[9] -1	0	0xdceb8000 - 0xdcebbfff (0x4000) MX[B]
	[10] -1	0	0xdcebfc00 - 0xdcebfcff (0x100) MX[B]
	[11] -1	0	0xdcebe000 - 0xdcebefff (0x1000) MX[B]
	[12] -1	0	0xdf6e0000 - 0xdf6fffff (0x20000) MX[B](B)
	[13] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[16] -1	0	0xdcec0000 - 0xdcefffff (0x40000) MX[B]
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[23] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[24] -1	0	0x00000700 - 0x0000073f (0x40) IX[B]
	[25] -1	0	0x00000600 - 0x0000063f (0x40) IX[B]
	[26] -1	0	0x0000dc00 - 0x0000dc7f (0x80) IX[B](B)
	[27] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[28] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "RenderAccel" "True"
(**) NVIDIA(0): Option "AllowGLXWithComposite" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(==) NVIDIA(0): Using HW cursor
(**) NVIDIA(0): Enabling RENDER acceleration
(==) NVIDIA(0): Video key set to default value of 0x101fe
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

---

### Post by tseliot on 2007-05-07
try with:
```
sudo depmod -a
```

and if this doesn't work, post the output of:
```
sudo modprobe nvidia
```

---

### Post by darkmaster on 2007-05-07
> **tseliot said:**
> try with:
```
sudo depmod -a
```

and if this doesn't work, post the output of:
```
sudo modprobe nvidia
```

uhmm.... I'm not sure I got it right.
I was running the nv driver. I pressed alt-f1, stopped gdm, installed the nvidia driver using envy tryed to start the server, nothing.
I stopped gdm again and used depmod -a. Tryed to start the server, nothing, same error. 
So I stopped gdm again, tryed modprobe and there was no outpoot at all. So I tryed to start gdm and nothing, same error. Did I do something wrong? :confused:

---

### Post by SeanHodges on 2007-06-02
Wrong box, sorry!

---

