---
title: "Nvidia GeForce 2 MX400 - nvidia Restricted Driver troubles"
date: 2007-10-29
forum: Hardware &amp; Laptops
---

### Post by Popidge on 2007-10-29
Hi, i recently got hold of an Nvidia GeForce 2 MX/MX 400 card (free of charge - result!), and happily installed it. Booted up M$ WinXP, worked fine, got the official NVidia driver installed, worked perfectly. No problem there.

Booted into Ubuntu (7.10), worked fine using the "nv" driver, but then i decided to install the restricted driver that was available (which i noticed was "nvidia-glx" whilst it was installing)
Rebooted, splash screen was fine, but then i got a flashing black+white screen with lines instead of my usual login screen. However, i heard the "Ready" sound and so i though that maybe logging in would possibly help, so i did, and the screen was still the same, a few shape changes, but the "login" sound played, and i can assume i was at my ubuntu desktop (but i might as well have been blind for all i care, couldn't see anything at all)

So what's up? After looking through the forums and the wiki, all i can see that could point me in the right direction is that the nvidia-glx driver no longer supports the Geforce 2 MX/MX400, as Nividia consider it a Legacy product nowadays. Is that the problem? If so, how do i change that setting to something that works? Will i have to switch back to the "nv" driver before installing the "nvidia-legacy-glx" driver? How would i do that without going into my unusable Ubuntu GUI? I'm posting here in a Live Session (thank tux for LiveCD's) so if a soultion exists around that, then it's all good :)

Oh and if you want it (which you might, i don't know), here's my xorg.conf

```
Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV11 [GeForce2 MX/MX 400]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-51
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV11 [GeForce2 MX/MX 400]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1024x768"	"800x600"	"720x400"	"640x480"	"1x1"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection
```

Thanks all! :)
Now i'm off to watch a bit of TV, so i'll hopefully get back to your help later

---

### Post by justsomedude on 2007-10-29
Hey there, since I'm currently doing some reading on Nvidia Cards due to some problems (not related to yours), I figured I'd try to help you.

I'm no expert, so take this with a grain of salt...


Ok, first we bring your graphical environment back:

Boot, and then use Ctrl + Alt + F1 to switch to console.

Then login and enter 

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.backup
```

to backup your xorg.conf. This might sound superfluous as it doesn't work anyway, but you never know when it comes in handy...

Then do

```

sudo nano /etc/X11/xorg.conf
``` 

to edit your xorg.conf.

Change the following section:

```
Section "Device"
	Identifier	"nVidia Corporation NV11 [GeForce2 MX/MX 400]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection
```

to this:

```
Section "Device"
	Identifier	"nVidia Corporation NV11 [GeForce2 MX/MX 400]"
	Driver		"nv"
	Busid		"PCI:1:0:0"
	#Option		"AddARGBVisuals"	"True"
	#Option		"AddARGBGLXVisuals"	"True"
	#Option		"NoLogo"	"True"
EndSection
```

Save it and reboot, you should then be able to login graphically.


You can then try to automatically reconfigure your xorg.conf with

```
sudo nvidia-xconfig
```

although it looks fine above. 


nvidia-glx (NOT nvidia-glx-new) should be fine for your card. The legacy driver is not for MX cards as far as I have read, but you might do some research on that yourself...

---

### Post by Popidge on 2007-10-29
Awesome, thanks.

Booting then Ctrl+Alt+F1 didn't work, i got the splash as normal, but then the same problem, but that was easily worked around by booting into recovery mode, which automatically gave me root privileges. Then it was simple backing up and changing my xorg.conf, and i'm back onto my normal ubuntu installation, using the good ol' "nv" driver right now.
I'll do a little research into wether or not the legacy diver works (i'll d/l the one direct from Nvidia and manually install it, if it doesn't work then i supose i'll be back to "nv")

But thanks, it's nice to be back in my old GUI... recovery mode scares me slightly..

---

### Post by shadowlab on 2007-11-13
I have a similar situation. Have you come across a solution?

My Current Config:
- Fresh install of Ubuntu 7.10
- NVIDIA GeForce2 MX400 with a DVI and VGA port. I'm only using the DVI port with a LCD.

I've tried the restricted driver, Envy, and several other configurations that I've come across while searching the forums. After performing a reboot, each one results in just a black screen at the login prompt.

The only driver that seems to work is the no frills "nv" driver which isn't capable of anything worthwhile.

I've spent 10+ hours working on this and I'm determined to find something that works. Any other suggestions would be greatly appreciated.

Thanks.

---

### Post by Daelyn on 2007-11-14
> **shadowlab said:**
> I have a similar situation. Have you come across a solution?

My Current Config:
- Fresh install of Ubuntu 7.10
- NVIDIA GeForce2 MX400 with a DVI and VGA port. I'm only using the DVI port with a LCD.

I've tried the restricted driver, Envy, and several other configurations that I've come across while searching the forums. After performing a reboot, each one results in just a black screen at the login prompt.

The only driver that seems to work is the no frills "nv" driver which isn't capable of anything worthwhile.

I've spent 10+ hours working on this and I'm determined to find something that works. Any other suggestions would be greatly appreciated.

Thanks.

Try switching to Depth 16 instead of 24.
I have big issues switching to 24 on mine of some reason. The driver just dont accept it at boot..

So, when I need to use 24 bit (Enemy Territory, Quake Wars) I drop to a console, stop gnome, edit the xorg to 24 bit and then restart X it works fab. 

Just a tip, maybe could help you.

---

### Post by shadowlab on 2007-11-15
> **Daelyn said:**
> Try switching to Depth 16 instead of 24.
I have big issues switching to 24 on mine of some reason. The driver just dont accept it at boot..

So, when I need to use 24 bit (Enemy Territory, Quake Wars) I drop to a console, stop gnome, edit the xorg to 24 bit and then restart X it works fab. 

Just a tip, maybe could help you.


Thanks for the suggestion Daelyn. Unfortunately, the same black screen of death persists. It was worth a shot though.

---

### Post by Bruegger on 2007-11-16
Shadowlab,
What driver are you using?
Maybe you should try the patched 8776 drivers or install 96.43.1 through envy 0.9.8.
I have a geforce2 gpu and i am using the 96.43.1. I also tested the 8776 drivers and they work well too in gutsy. You can take your pick from either of the two.
Cheers!

---

### Post by Daelyn on 2007-11-16
> **shadowlab said:**
> Thanks for the suggestion Daelyn. Unfortunately, the same black screen of death persists. It was worth a shot though.

It must be down to a resolution/freq thingy. I always end up getting the same when I fiddle with my nvidia driver.

What happends if you disable the freq detection?

Could you please try to boot into ubuntu with the faulty settings, when you have a black screen drop to one of the consoles and type

```
 sudo cp /var/log/Xorg.0.log /var/log/Xorg.0.fail 
```

This will copy the faulty attempt to load xorg.

Reboot into vesa mode.

Open the fail Xorg log we just copied and paste it here in the forum under a code wrap. Would help diagnose greatly. Thanks.

---

### Post by Smartpal on 2007-11-21
I also have the same problem with the GeForce 2 MX/MX400...and I have to use the "nv" driver which dosen't allow any desktop effects...I even added the line Option "UseDisplayDevice" "DFP" under Section "Screen" in xorg.conf...still no luck..so I'm giving envy a shot now...I'll post back if it works..

---

### Post by Smartpal on 2007-11-21
no luck..guess I'm stuck with "nv" now..I'll just wait if you guys have a solution..:(

---

### Post by Daelyn on 2007-12-04
> **Smartpal said:**
> no luck..guess I'm stuck with "nv" now..I'll just wait if you guys have a solution..:(

Could you try copy that xorg log for us to see through? 
We'll benefit alot from seeing the error or no errors in that one.

Read my previous post and follow that instruction.
We'll investigate further, no worries.

---

### Post by shimmergloom on 2007-12-04
Hello, I am still rather new to Ubunutu and Linux in general.
I have been experiencing the black screen of death that shadowlab has.
I installed 7.10 gutsy 64 bit and then installed the linux source so that the driver i downloaded from the nvida site could compile stuff (it told me to do that the first time i tried to install it from the .run file) Then I tried to reboot after it was installed and the screen with the loading bar and ubuntu logo(the splash screen I am guessing) appears but after that it goes black.  I really would like to get it working so I can experience all the good stuff gusty has to offer. If you need any more information to make a diagnosis let me know what you need and I will try to get it to you.  Please include detailed directions on how to get the info you need since I am still a newbie.

FYI:  I have an nvidia geforce fx 5200 card and an amd 64 athalon processor so I have been trying to install the 64 bit nvidia driver from the nvidia site.

---

### Post by Lutin on 2007-12-04
Hi

Just thought that I would relate my own experiences with the nVidia driver and GeForce 2 MX400 card.

Initially, I had a load of problems too and much head scratching followed whilst trying to sort it out. Anyway, I posted a question on another thread - that I cannot find now - that lead to an answer, well for me anyway.

I presume that you are trying to use the downloaded nVidia driver, rather than that offered by synaptic?

So, download driver to handy directory - usually somewhere in /home. You will need a number of other packages for the driver to do it's thing - libc6 comes to mind. I think they are all in the build-essential package.

As root - I usual boot into the "Recovery Mode" - stop Gnome.

/etc/init.d/gdm stop

Change directory to where you left the downloaded nVidia driver and run the script -

sh ./NVIDIA-LInux-***************.run

Now, before rebooting the computer, change to directory -

/lib/linux-restricted-modules/2.6.22-14-generic

Here you may well find three nvidia directories -

nvidia  nvidia_legacy  and   nvidia_new

Now this is where I managed to get the driver working, as two of my computers will not start X with all three of these nvidia directories in place. To be on the safe side rename two of them - to anything you like but not starting with nvidia, I just renamed them Xnvidia etc.

I have been successful with using the nvidia_new directory (and renaming the other two directories) on two of my computers.

Just for the record -

nVidia GeForce 2 MX400

nVidia driver - 1.0-9639

Ubuntu Gutsy Gibbon 7.10

I can post my xorg.conf file if anyone thinks that it will help.

By the way, I have found no explanation as to why there should be these three nvidia directories or indeed why they can cause so much trouble.

Anyway, this might help someone - and that's what we are here for right?

---

### Post by fackaff on 2007-12-05
hey guys i just went thru the same problem
same graphic card same errors, etc etc...
i thot mayb the problems were being cause because some libc6-dev files werent reverse-compatible with libc6 ...one was ubuntu9 and the other was ubuntu10...
im a newbie at all this

i figured there was a problem with new versions of some system files...

so i reinstalled xubuntu and dint update any files...without updating files, nvidia drivers, compiz fusion everyding installed damn smoothly...

mayb u guys can try reinstalling and not updating anything ...

enable the restricted driver ...and then BINGO!

---

### Post by fackaff on 2007-12-06
ok great....i restarted xubuntu...and im back with the same error as previously...ubuntu is running in low-graphics mode....
plz for gods sake some1 help me solve this problem...
i just cant enable the nvidia driver properly...
always end up getting the low graphics mode

---

### Post by jenkinbr on 2007-12-10
Thank you Lutin for the detailed instructions.  I used them to install nvidia driver NVIDIA-Linux-x86-93.43.01-pkg1.run for my GeForce 2 MX400.

All started out well, I downloaded the package to my home directory, booted into recovery mode, ran the script, and rebooted (forgot to move the folders at this point.)

All seemed well at first, I got a message saying that I was running non-free drivers, I knew that.  Just to verify the install, I did a restart, and was put into low-graphics mode.

At this point, I realized I had forgotten to move two of the three "nvidia*" directories.  So I rebooted to recovery, moved "nvidia" and "nvidia_legacy", and rebooted.  Still broken.  Back in recovery mode, I started over.  I re-ran the script, allowing it to uninstall the previous drivers in the process.  I then switched over to /lib/linux-restricted-modules/2.6.22-14-generic/ and moved "xnvidia" and "xnvidia_legacy" (the originals were not recreated!?) to "xnv" and "xnv_lgcy" just to be on the safe side.

Several reboots proved that this seemed to have worked.  Right now, I am just glad I could offload graphics processing and use my 1.5 GHz to do more useful things.  The only question I have is this: Can you run desktop effects at all using this card?  I get an error saying that my hardware does not support desktop effects.  My geuss is that this outdated card isn't capable enough, but I just wanted to see what others had to say on it.

---

### Post by fackaff on 2007-12-10
xubuntu 7.10 users...use envy for the exact same graphic card...
it works like a charm!

---

### Post by Sweet Spot on 2007-12-10
> **fackaff said:**
> xubuntu 7.10 users...use envy for the exact same graphic card...
it works like a charm!

That's exactly what I did (same card as you guys) but it screwed up my refresh rate options and only offered me 50Hz compared to 75. So I uninstalled the driver that Envy chose, and reconfigured Xorg to what it was before. Now I have my 1440x900 res @75 Hz. 

But, I am only working with the standard nv drivers at 1/2 the 24bit depth according to the configuration editor. 

Question about the restricted drivers... I believe that it had been using the glx driver previously, so I guess I can just install that from Synaptic, but can't I also just (as suggested above) enable "restricted drivers" ? And where the heck is that again ?

Nevrmind.. I see where it would be, but it's gone from the list. So I guess I have to get it from Synaptic.

---

### Post by Lutin on 2007-12-11
jenkinbr

I must admit that I hadn't tried any visual effects as I am not particulary interested in them. But I have just tried them and yes I am getting some odd behaviour. For instance, using "Normal" visual effects, the minimise and maximise buttons on my windows disappear. I didn't bother trying any other settings after finding this.

regards

---

### Post by jenkinbr on 2007-12-11
No problem.  I wouldn't want to disrupt my system over such a small issue.  With this card, the eye candy would probably cause a slowdown anyways...

Thanks for trying, though.

---

### Post by shadowlab on 2007-12-11
> **Daelyn said:**
> It must be down to a resolution/freq thingy. I always end up getting the same when I fiddle with my nvidia driver.

What happends if you disable the freq detection?

Could you please try to boot into ubuntu with the faulty settings, when you have a black screen drop to one of the consoles and type

```
 sudo cp /var/log/Xorg.0.log /var/log/Xorg.0.fail 
```

This will copy the faulty attempt to load xorg.

Reboot into vesa mode.

Open the fail Xorg log we just copied and paste it here in the forum under a code wrap. Would help diagnose greatly. Thanks.

Hey Daelyn, sorry for not replying sooner. The forum didn't send me an email saying someone had responded. I'm not sure how to disable the frequency detection, but I'm assuming that option is in the xorg.conf (included at the bottom of this post) so feel free to tell me what I should try editing.

I tried installing the drivers again using Envy combined with Lutin's suggestion of renaming the other 2 nvidia directories, but I'm still getting the black screen o' death.

Thanks for all your help!!

Here is the Xorg.0.fail as you requested:
```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux winklebottom 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Dec 11 19:24:25 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "nVidia Corporation NV11 [GeForce2 MX/MX 400]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81ea440
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2530 card 0000,0000 rev 04 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2532 card 0000,0000 rev 04 class 06,04,00 hdr 01
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 04 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,2440 card 0000,0000 rev 04 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,244b card 107b,0116 rev 04 class 01,01,80 hdr 00
(II) PCI: 00:1f:2: chip 8086,2442 card 107b,0116 rev 04 class 0c,03,00 hdr 00
(II) PCI: 00:1f:3: chip 8086,2443 card 107b,0116 rev 04 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0110 card 1462,8837 rev b2 class 03,00,00 hdr 00
(II) PCI: 02:01:0: chip 1033,0035 card 107b,0116 rev 41 class 0c,03,10 hdr 80
(II) PCI: 02:01:1: chip 1033,0035 card 107b,0116 rev 41 class 0c,03,10 hdr 00
(II) PCI: 02:01:2: chip 1033,00e0 card 107b,0116 rev 02 class 0c,03,20 hdr 00
(II) PCI: 02:08:0: chip 8086,2449 card 8086,3013 rev 03 class 02,00,00 hdr 00
(II) PCI: 02:0b:0: chip 104c,8020 card 1545,0401 rev 00 class 0c,00,10 hdr 00
(II) PCI: 02:0c:0: chip 1102,0002 card 1102,8032 rev 07 class 04,01,00 hdr 80
(II) PCI: 02:0c:1: chip 1102,7002 card 1102,0020 rev 07 class 09,80,00 hdr 80
(II) PCI: 02:0d:0: chip 14e4,4212 card 14e4,0002 rev 00 class 07,03,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfc900000 - 0xfe9fffff (0x2100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe4600000 - 0xf46fffff (0x10100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfea00000 - 0xfeafffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xf4700000 - 0xf47fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV11 [GeForce2 MX/MX 400] rev 178, Mem @ 0xfd000000/24, 0xe8000000/27, BIOS @ 0xfe9f0000/16
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
(II) PCI Memory resource overlap reduced 0xf8000000 from 0xfbffffff to 0xf7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfeaf7000 - 0xfeaf7fff (0x1000) MX[B]
	[1] -1	0	0xfeaf8000 - 0xfeafbfff (0x4000) MX[B]
	[2] -1	0	0xfeaff000 - 0xfeaff7ff (0x800) MX[B]
	[3] -1	0	0xfeafc000 - 0xfeafcfff (0x1000) MX[B]
	[4] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[5] -1	0	0xfeafe000 - 0xfeafefff (0x1000) MX[B]
	[6] -1	0	0xfeafd000 - 0xfeafdfff (0x1000) MX[B]
	[7] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[8] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[9] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[10] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000dfa0 - 0x0000dfaf (0x10) IX[B]
	[12] -1	0	0x0000dff0 - 0x0000dff7 (0x8) IX[B]
	[13] -1	0	0x0000df80 - 0x0000df9f (0x20) IX[B]
	[14] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[15] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[16] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[17] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfeaf7000 - 0xfeaf7fff (0x1000) MX[B]
	[1] -1	0	0xfeaf8000 - 0xfeafbfff (0x4000) MX[B]
	[2] -1	0	0xfeaff000 - 0xfeaff7ff (0x800) MX[B]
	[3] -1	0	0xfeafc000 - 0xfeafcfff (0x1000) MX[B]
	[4] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[5] -1	0	0xfeafe000 - 0xfeafefff (0x1000) MX[B]
	[6] -1	0	0xfeafd000 - 0xfeafdfff (0x1000) MX[B]
	[7] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[8] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[9] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[10] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000dfa0 - 0x0000dfaf (0x10) IX[B]
	[12] -1	0	0x0000dff0 - 0x0000dff7 (0x8) IX[B]
	[13] -1	0	0x0000df80 - 0x0000df9f (0x20) IX[B]
	[14] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[15] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[16] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[17] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
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
	[4] -1	0	0xfeaf7000 - 0xfeaf7fff (0x1000) MX[B]
	[5] -1	0	0xfeaf8000 - 0xfeafbfff (0x4000) MX[B]
	[6] -1	0	0xfeaff000 - 0xfeaff7ff (0x800) MX[B]
	[7] -1	0	0xfeafc000 - 0xfeafcfff (0x1000) MX[B]
	[8] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[9] -1	0	0xfeafe000 - 0xfeafefff (0x1000) MX[B]
	[10] -1	0	0xfeafd000 - 0xfeafdfff (0x1000) MX[B]
	[11] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[12] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[13] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[14] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000dfa0 - 0x0000dfaf (0x10) IX[B]
	[18] -1	0	0x0000dff0 - 0x0000dff7 (0x8) IX[B]
	[19] -1	0	0x0000df80 - 0x0000df9f (0x20) IX[B]
	[20] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[21] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[22] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[23] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  96.43.01  Wed Sep  5 19:47:01 PDT 2007
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) NVIDIA dlloader X Driver  96.43.01  Wed Sep  5 19:14:11 PDT 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeaf7000 - 0xfeaf7fff (0x1000) MX[B]
	[5] -1	0	0xfeaf8000 - 0xfeafbfff (0x4000) MX[B]
	[6] -1	0	0xfeaff000 - 0xfeaff7ff (0x800) MX[B]
	[7] -1	0	0xfeafc000 - 0xfeafcfff (0x1000) MX[B]
	[8] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[9] -1	0	0xfeafe000 - 0xfeafefff (0x1000) MX[B]
	[10] -1	0	0xfeafd000 - 0xfeafdfff (0x1000) MX[B]
	[11] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[12] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[13] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[14] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000dfa0 - 0x0000dfaf (0x10) IX[B]
	[18] -1	0	0x0000dff0 - 0x0000dff7 (0x8) IX[B]
	[19] -1	0	0x0000df80 - 0x0000df9f (0x20) IX[B]
	[20] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[21] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[22] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[23] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeaf7000 - 0xfeaf7fff (0x1000) MX[B]
	[5] -1	0	0xfeaf8000 - 0xfeafbfff (0x4000) MX[B]
	[6] -1	0	0xfeaff000 - 0xfeaff7ff (0x800) MX[B]
	[7] -1	0	0xfeafc000 - 0xfeafcfff (0x1000) MX[B]
	[8] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[9] -1	0	0xfeafe000 - 0xfeafefff (0x1000) MX[B]
	[10] -1	0	0xfeafd000 - 0xfeafdfff (0x1000) MX[B]
	[11] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[12] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[13] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[14] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000dfa0 - 0x0000dfaf (0x10) IX[B]
	[21] -1	0	0x0000dff0 - 0x0000dff7 (0x8) IX[B]
	[22] -1	0	0x0000df80 - 0x0000df9f (0x20) IX[B]
	[23] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[24] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[25] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[26] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[27] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[28] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce2 MX/MX 400 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 65536 kBytes
(--) NVIDIA(0): VideoBIOS: 03.11.01.30.41
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are not supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce2 MX/MX 400 at
(--) NVIDIA(0):     PCI:1:0:0:
(--) NVIDIA(0):     Gateway FPD1810 (DFP-0)
(--) NVIDIA(0): Gateway FPD1810 (DFP-0): 65.0 MHz maximum pixel clock
(--) NVIDIA(0): Gateway FPD1810 (DFP-0): Internal Single Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 640 x 480
(--) NVIDIA(0): DPI set to (45, 42); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe8000000 - 0xefffffff (0x8000000) MX[B]
	[1] 0	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xfeaf7000 - 0xfeaf7fff (0x1000) MX[B]
	[7] -1	0	0xfeaf8000 - 0xfeafbfff (0x4000) MX[B]
	[8] -1	0	0xfeaff000 - 0xfeaff7ff (0x800) MX[B]
	[9] -1	0	0xfeafc000 - 0xfeafcfff (0x1000) MX[B]
	[10] -1	0	0xfeaffc00 - 0xfeaffcff (0x100) MX[B]
	[11] -1	0	0xfeafe000 - 0xfeafefff (0x1000) MX[B]
	[12] -1	0	0xfeafd000 - 0xfeafdfff (0x1000) MX[B]
	[13] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[14] -1	0	0xfe9f0000 - 0xfe9fffff (0x10000) MX[B](B)
	[15] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[16] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000dfa0 - 0x0000dfaf (0x10) IX[B]
	[23] -1	0	0x0000dff0 - 0x0000dff7 (0x8) IX[B]
	[24] -1	0	0x0000df80 - 0x0000df9f (0x20) IX[B]
	[25] -1	0	0x0000df00 - 0x0000df3f (0x40) IX[B]
	[26] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[27] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[28] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[29] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[30] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Built-in logo is bigger than the screen.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(WW) NVIDIA(0): WAIT (0, 1, 0xffff, 0x00000490, 0x00000490)
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
```

Also, here's the xorg.conf that Envy generated:
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Sep  5 19:29:10 PDT 2007

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

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV11 [GeForce2 MX/MX 400]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV11 [GeForce2 MX/MX 400]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

---

### Post by [Knuckles] on 2007-12-29
Hey.

I was just building a computer with my old geforce 2 mx 400 and had this problem too.

Tried many things, but in the end I gave up and installed a geforce 4 mx, and it started working immediately, including aiglx.

This is a NVIDIA BUG, and nobody seems to notice it.

---

### Post by shadowlab on 2007-12-30
> **'[Knuckles] said:**
> Hey.

I was just building a computer with my old geforce 2 mx 400 and had this problem too.

Tried many things, but in the end I gave up and installed a geforce 4 mx, and it started working immediately, including aiglx.

This is a NVIDIA BUG, and nobody seems to notice it.

Plenty of people have noticed. It just seems that no one at NVIDIA seems to care about fixing it. ](*,)

---

### Post by esmerine on 2008-01-08
```
Section "Device"
    Identifier     "nVidia Corporation NV11 [GeForce2 MX/MX 400]"
    Driver         "nvidia"
    BoardName      "nv"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
 #   
    Identifier     "device1"
    Driver         "nvidia"
    BoardName      "nv"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection
```

That means I'm using nv driver, I guess? O:)
When I was trying to enable effects, titlebars disappeared. Then I found some solution I don't remember. Then titlebars appeared. Effects ran, not very smoothly and used almost 100% of cpu. Friend said: "that's not how the effects are supposed to look like." Don't know how much he knows about this but I personally thought that this card isn't capable of doing perfectly smooth effects :D.
And now I'm affraid of changing the driver.

What about openGL 2.0 with "nv" driver?

---

### Post by [Knuckles] on 2008-01-08
> **esmerine said:**
> ```
Section "Device"
    Identifier     "nVidia Corporation NV11 [GeForce2 MX/MX 400]"
    Driver         "nvidia"
    BoardName      "nv"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
 #   
    Identifier     "device1"
    Driver         "nvidia"
    BoardName      "nv"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection
```

That means I'm using nv driver, I guess? O:)
When I was trying to enable effects, titlebars disappeared. Then I found some solution I don't remember. Then titlebars appeared. Effects ran, not very smoothly and used almost 100% of cpu. Friend said: "that's not how the effects are supposed to look like." Don't know how much he knows about this but I personally thought that this card isn't capable of doing perfectly smooth effects :D.
And now I'm affraid of changing the driver.

What about openGL 2.0 with "nv" driver?

You have a very strange xorg.conf, but indeed you are using the nv driver. The titlebars you saw disappearing when trying to enable effects was probably metacity (the default gnome window manager) that was closed, but compiz (the compositing manager, the app responsible for all those fancy effects) failed to start.

Anyways, opengl is possible with the nv driver, but all opengl calls are processed by the cpu, so all effects should be very slow (how slow depends on your cpu). I'm guessing that you have Xgl installed, because as far as I know only Xgl allows effects to work with software opengl.

So, for now, the nvidia-glx driver should crash for you too, but you could try installing the nvidia-glx-legacy driver, which may work (I finished building the system I had the problem with using a geforce 4, didn't had the chance try to use that driver).

Finally, as it crashes a bit hard, I would recommend that you only try to change the driver if you can make a backup of your xorg.conf, and know how restore it using the command-line.

Edit: Just for curiosity, you can use the following command to see if the card is using direct rendering (if it is, then 3d is ok, if it is not, 3d is using cpu and not using gpu at all)
k@l~> glxinfo | grep direct
direct rendering: Yes

---

### Post by esmerine on 2008-01-08
Thanks!
Why my xorg file is weird? (:

It says that the card uses direct rendering. Okay, I'll try to install the other driver when I learn how to restore everything.There is a backup file already made earlier.

---

### Post by [Knuckles] on 2008-01-09
Heh, sorry, just got up and realised that yesterday I must've been really sleepy.

The line that really matters is:
    Driver         "nvidia"
Which obviously reveals that you are using the nvidia binary driver, and not the nv open-source one.

As for your troubles with effects, I may be able to help, but if you already have working 3d drivers I'm guessing there are lots of threads helping to solve problems related to 3d effects.

---

### Post by shadowlab on 2008-06-11
My restricted driver problem has been solved...kind of!

In my case, the major problem with the restricted driver for my NVIDIA GeForce 2 MX400 card was due to my use of the DVI cable with my Gateway FPD1810 LCD monitor.

I suspected this was the problem all along, but I tried and tried in vain to make it work with DVI. I finally gave in and decided to use the VGA port instead and whola...it works! No more black screen of death. It's isn't exactly the ideal solution I was looking for, but it works, so for those of you with a similar situation you might want to just try using VGA instead, if that's an option.

Happy trails and best of luck to all of you. I spent many a frustrated day on this, but thankfully I can close this chapter once and for all.

---

