---
title: "[SOLVED] Where has the screen and graphics package gone??"
date: 2008-11-07
forum: General Help
---

### Post by dai_trying on 2008-11-07
Hello to all, I am relatively new to ubuntu/linux but have been trying to get everything working without having to post too often. (Nearly always I have found solutions to my problems within other posts) 

Anyway back to my problem...

I have been using Ubuntu 8.04 and enjoying the experience, however, I downloaded and installed 8.10 as I tested the live cd and it seemed to be ok. But now I cannot change my screen resolution above 800*600. I did have the same problem when I first installed 8.04 but read of "screen and graphics" option to tell ubuntu what monitor I was using. I selected the monitor manafacturer and model and hey presto up to 1280 * 1024 worked a treat. But I cannot find this option anymore.........
Any help would be greatly appreciated..

Many thanks
Dave

System:- Compaq presario 6000 with dell 17"lcd screen

lspci returns

00:00.0 Host bridge: nVidia Corporation nForce CPU bridge (rev b2)
00:00.1 RAM memory: nVidia Corporation nForce 220/420 Memory Controller (rev b2)
00:00.2 RAM memory: nVidia Corporation nForce 220/420 Memory Controller (rev b2)
00:00.3 RAM memory: nVidia Corporation Device 01aa (rev b2)
00:01.0 ISA bridge: nVidia Corporation nForce ISA Bridge (rev c3)
00:01.1 SMBus: nVidia Corporation nForce PCI System Management (rev c1)
00:02.0 USB Controller: nVidia Corporation nForce USB Controller (rev c3)
00:03.0 USB Controller: nVidia Corporation nForce USB Controller (rev c3)
00:04.0 Ethernet controller: nVidia Corporation nForce Ethernet Controller (rev c2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce AC'97 Audio Controller (rev c2)
00:08.0 PCI bridge: nVidia Corporation nForce PCI-to-PCI bridge (rev c2)
00:09.0 IDE interface: nVidia Corporation nForce IDE (rev c3)
00:1e.0 PCI bridge: nVidia Corporation nForce AGP to PCI Bridge (rev b2)
01:00.0 VGA compatible controller: nVidia Corporation NVCrush11 [GeForce2 MX Integrated Graphics] (rev b1)
02:06.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
02:06.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
02:07.0 Communication controller: Conexant Systems, Inc. HSF 56k HSFi Modem (rev 01)

---

### Post by overdrank on 2008-11-07
Hi and welcome, Have you tried to use Envy to install the drivers?
You may also try and boot into recovery mode, which is usually the second choice from the grub and use the xfix option to correct the graphics issues.

---

### Post by philinux on 2008-11-07
Screens and graphics was removed for Intrepid. Replaced by jockey-gtk

System>Admin>Hardware Drivers

---

### Post by dai_trying on 2008-11-07
Thanks for the replies, I'm afraid I'm still no nearer. I haven't used envy before and cannot find it in the add/remove applications. rebooting to recovery and running xfix didn't appear to make a difference either.
I have (apparently) got jockey installed (although there were 2 instances 1 for gnome the other kde I have the gnome one but presume they will be the same just a different front end?) but when I go to system>admin>hardware drivers there are no proprietry drivers installed.
I have a clean install so this wasn't really unexpected.
I have read quite a few posts offering what seems quite long winded workarounds, but I am trying to do as much as possible from the gui.

Many thanks again.
Dave

Just a note to end my question. I have reverted to 8.04 as I was getting close to throwing the box out the window... how did we manage before high resolution??? thanks for the help tho and I will be keeping my eyes peeled for anyone who resolves similar issues.
Thanks to moderators for keeping this extremely useful forum going. Keep up the great work.

Dave

---

### Post by dai_trying on 2008-11-26
Hi everyone, Just in case anyone has similar problems to me, I have now solved my display problem. 
I re-installed hardy and copied my xorg.conf (and saved it).
then wiped hardy again and installed intrepid
then copied what I thought were relevant parts of xorg.conf to the current file.
I did not have to install 3rd party drivers (YAY)
and after a few beads of sweat and few mugs of caffeine she fired on all cylinders and I can now see again.

Here are before and after xorg.conf info.

BEFORE

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

AND THIS IS NOW

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"NVIDIA GeForce2 Integrated (generic)"
	Busid		"PCI:1:0:0"
	Screen	0
	Vendorname	"NVIDIA"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Dell"
	Modelname	"Dell E171FP"
	Horizsync	30.0-80.0
	Vertrefresh	56.0-76.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	1024
		Modes		"800x600@60"	"832x624@75"	"800x600@75"	"1024x768@75"	"800x600@72"	"1024x768@70"	"800x600@56"	"1024x768@60"	"640x480@75"	"1152x864@75"	"640x480@72"	"1280x1024@75"	"640x480@60"	"1280x960@60"	"1280x1024@60"	"1280x960@75"
	EndSubSection
EndSection

I hope this post may come in handy to anyone whose edid info is not present or available. This (I think) is what caused my problem in the first place
Many thanks to the numerous other posts that have led me to my conclusion.
Dave

---

