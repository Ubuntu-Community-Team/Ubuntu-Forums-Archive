---
title: "[SOLVED] Cannot enable visual effects ATI X1650 Pro"
date: 2008-11-08
forum: General Help
---

### Post by Merovius on 2008-11-08
I have Ubuntu 8.10 installed. I have installed the proprietery drivers through the restricted drivers manager and with Envy. The system boots fine.

If I enable visual effects the panels and all desktop icons vanish. I have to revert to no effects to have a desktop.

I have installed this video card in another machine and enabled the visual effects with no trouble. I even used remastersys to install a live version of this machine onto the other and the drivers worked fine.

Could it be that my motherboard chipset when combined with ATI X1650 Pro and Ubuntu 8.10 will not work together?? 

This is what my xorg.conf file looks like


Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
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

Runs fine in non 3D mode. But cannot enable effects.

Ideas? Suggestions? :confused:

---

### Post by Merovius on 2008-11-08
Forgot to mention my board is an Asus K8N-E.

TIA

---

### Post by Merovius on 2008-11-08
I ran compix-check and got these results. looks like it should work..

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV535 [Radeon X1650 Series] (rev 9e)
 Driver in use:         fglrx
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

---

### Post by eternalnewbee on 2008-11-08
Press ALT-F2 and paste this code: ```
compiz --replace
``` and see if it starts up

---

### Post by Merovius on 2008-11-09
Oh, it starts, then I have no panels or icons on the desktop as I said in the first post.

Just the background image. It seems that the desktop image comes to the front and hides the actual desktop. I can tell that there are things behind the image by mousing over the image.

I don't get it.

---

### Post by Merovius on 2008-11-09
This is what I get when I enable effects.

[IMG]https://cid-8e09383c4ac6f893.skydrive.live.com/self.aspx/Pictures/Screen%20Shots/Screenshot-1.jpg[/IMG]

---

### Post by Merovius on 2008-11-09
[attach]91829[/attach]

Sorry about that. As you can see everything disappears.

---

### Post by eternalnewbee on 2008-11-09
The only thing left that I can think of: 
Install the Compiz-Fusion Icon.
After the installation is complete, Go to Main Menu > System Tools, and click on it. If everything goes well, the blue icon will appear in the notification area on the right in your panel. Right-click on it and under Select Window Manager select Compiz. sorry I can't be of more help at this moment.

---

### Post by Merovius on 2008-11-09
Same old thing. Poof no panels or icons...:(

---

### Post by eternalnewbee on 2008-11-09
I don't even think this is relevant, but just to be sure: Is your Hardware Driver enabled?
To check: **Main Menu > System > Administration > Hardware Drivers**.

---

### Post by Merovius on 2008-11-09
Yup. enables with no problem. Just can't turn on visual effects under appearance.

I'm about to give up and go back to Nvidia. I've tried this card a couple times now and it will not work correctly in this machine. (Works in my older machine.)

---

### Post by Merovius on 2008-11-09
Another thing I tried out of desperation was a clean Ibex install. The live disk loads and I tell it to install. A short bit into the install the monitor goes black and displays "no signal" Then I had to reset to get out of it. Fortunately it didn't hose my system. 

I've just about come to the conclusion that this card will not work in this board under Ubuntu 8.10.

---

### Post by Merovius on 2008-11-09
Well after 10 to 11 hours of trying I pulled the ATI X1650 Pro and went back to the Nvidia 6800XE. It was installed and enabled to full effect in about 15 minutes.

I guess that will teach me to use NVIDIA. ](*,)

---

### Post by eternalnewbee on 2008-11-09
Sorry man, I feel your frustration
EDIT: Talk about timing!

---

### Post by Merovius on 2008-11-09
Thanks again for the help you gave. Ironically I put the ATI card in my old system and enabled the driver. Poof visual effects were enabled by DEFAULT....... :twisted:

lol

---

