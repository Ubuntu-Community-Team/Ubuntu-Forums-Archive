---
title: "Monitor Dims on X startup with GeForce 6200"
date: 2005-07-10
forum: Hardware &amp; Laptops
---

### Post by phzi on 2005-07-10
I purchased and installed a BFG GeForce 6200 vid card today, with the intent to replace my Radeon 9500 Pro so as to get better multimonitor support out of my Ubuntu installation.

To ease the installation of the new card, I decided to backup my relivent data, and simply do a fresh install of Ubuntu 5.04, so as to avoid any possible problems after the transition.

Ubuntu detected the NV card fine, and installation was smooth. Xorg ran perfectly.

I proceeded to install the NVidia drivers by the following proccess:
- apt-get install nvidia-glx
- apt-get install nvidia-settings
- nvidia-glx-config enable

The installation went as would be expected - no errors or warnings.

I proceeded to restart the X server, and things started going wrong. X seemed to load fine (nvidia logo displayed, and gnome login screen came up). However, the screen was so dimmed that it was not readable. The background image was barely distiguishable, as if the brightness had be turned to it's absolute lowest values.

Follows is information which I feel may be relivent:
LsPCI output: 
[PHP]0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0221 (rev a1)[/PHP]

xorg.conf file (relivent sections) Nvidia Installer Config:[PHP]
Section "Device"
	Identifier	"NVIDIA Corporation NV40? [Unknown nVidia Card]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV40? [Unknown nVidia Card]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection
[/PHP]

Only difference with working config, is that 	
Driver		"nvidia"
Driver		"nv"


Has anyone seen this problem, or know of a solution? I have no idea what could be causing this.

Thank-you in advance,
-phzi

---

### Post by phzi on 2005-07-10
I figured, since the screen dims when the nvidia logo displays, maybe the boot logo is actually the problem.

I added the followig line to my xorg.conf file:
        Option		"NoLogo"

No such luck, no logo, but still, the screen is too dim to see.

-phzi

---

### Post by mctavish on 2005-07-10
That would be the 6200 agp chipset which I have. It is a known problem, at least with the 7174 drivers. There is plenty of info at  the nvidia forum.

I'm just starting to look into it again after a few weeks and it looks like perhaps new drivers have been released by nvidia that support this chipset (7667), but they haven't made it into hoary backports because of a buggy reputation.

---

### Post by phzi on 2005-07-11
Well, I got mine working (with dual header too).

Just upgraded to the 7667 drivers from the nvidia installer, and haven't had any problems.

Cheers,
-phzi

---

