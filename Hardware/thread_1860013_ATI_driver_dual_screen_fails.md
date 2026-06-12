---
title: "ATI driver dual screen fails"
date: 2011-10-14
forum: Hardware
---

### Post by PhonicLynx on 2011-10-14
Just did a clean install of 11.10 and I can't get the dual monitor to install. The drivers install but I'm not 100% sure how well as says it can't write to some files. I've tried wiping and re installing with the additional drivers and then wiping and re installing with the ATI downloaded drivers 11.9. Both give me the same effect.

The driver can see that the computer has 2 monitors and they are sitting on the one card (as there are two running in crossfire). It gives me the option to make the extended desktop but as soon as I click either OK or APPLY the ACC closes and crashes. It doesn't seem to do anything at all.

Any ideas?

---

### Post by collisionystm on 2011-10-14
Run aticonfig in terminal

read towards the bottom

Look for and use the Dual Head config

---

### Post by PhonicLynx on 2011-10-14
I don't know which one to pick.. I tried a few of them and always got two white screens which didn't help cuz all I could to was switch to TTY1 and reconfigure it.

The only way I could get back was to delete /etc/X11/xorg.conf and reboot.

Also what is the service that runs the gui now? its no longer gdm?

---

### Post by collisionystm on 2011-10-14
Its lightdm

---

### Post by PhonicLynx on 2011-10-14
well i got the dual monitor to work and can now kinda use it but it dosn't work ultra well.

I used the command:
```
sudo aticonfig --initial --heads=2 --adapter=1 --xinerama=on
```

When I start lightdm I loose all unity until I do a full reboot. And then I loose all the transparency on everything. At first boot up the mouse and other graphics are really really slow and jerky.. but after around 30 or so secs they become okay to use.

The other thing i've noticed is that it almost appears as though there are 3 screens on the desktop but I can't see how that is because the ATI driver CCM reports xinerama as being on and only using 2 desktops.

---

### Post by PhonicLynx on 2011-10-14
This is what the xorg.conf comes out as.
```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	Screen         "aticonfig-Screen[0]-1" RightOf "aticonfig-Screen[0]-0"
	Screen         "aticonfig-Screen[1]-0" RightOf "aticonfig-Screen[0]-1"
	Screen         "aticonfig-Screen[1]-1" RightOf "aticonfig-Screen[1]-0"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "on"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-1"
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

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:4:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-1"
	Driver      "fglrx"
	BusID       "PCI:4:0:0"
	Screen      1
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]-0"
	Driver      "fglrx"
	BusID       "PCI:5:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]-1"
	Driver      "fglrx"
	BusID       "PCI:5:0:0"
	Screen      1
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
	Identifier "aticonfig-Screen[0]-1"
	Device     "aticonfig-Device[0]-1"
	Monitor    "aticonfig-Monitor[0]-1"
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

Section "Screen"
	Identifier "aticonfig-Screen[1]-1"
	Device     "aticonfig-Device[1]-1"
	Monitor    "aticonfig-Monitor[1]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

---

### Post by PhonicLynx on 2011-10-14
By removing all references to:
```
Screen         "aticonfig-Screen[1]-0" RightOf "aticonfig-Screen[0]-1"
	Screen         "aticonfig-Screen[1]-1" RightOf "aticonfig-Screen[1]-0"
```

it gave me back 2 screens and not 4 like it should have.

Having said that though.... there is no transparency anywhere and that really distracts from the whole unity looks okay now effect. 

Pressing the super key gives me a black box... 
Showing the whats on the desktops gives me a weird looking black screen and the side bar is well black with icons... 
The dbus notifications have an awquard black ring around them.

Is there any way to fix this because in single screen mode all that works fine... is it a driver thing?

---

### Post by PhonicLynx on 2011-10-14
Well I think I just figured it all out.. Wasn't quite what I expected.. I loaded up the CCM again and this time it didn't crash when I asked for it to go dual monitor. However I had to turn xinarama off in the config file for it to be able to edit it.

The resulting config file is this:
```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "0-DFP1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1920x1200"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-DFP3"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1920x1200"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "1920 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "Monitor-DFP1" "0-DFP1"
	Option	    "Monitor-DFP3" "0-DFP3"
	BusID       "PCI:4:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-1"
	Driver      "fglrx"
	BusID       "PCI:4:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual   3840 1920
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-1"
	Device     "aticonfig-Device[0]-1"
	Monitor    "aticonfig-Monitor[0]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

---

### Post by ggx123qwe on 2011-10-15
Had the same problem with you. Clean install 11.10 and Catalyst 11.9.CCC open but doesn do anything. Tried to aticonfig on terminal, lost all transparency, compiz fails, and everything feels jerky and jumpy. 

11.9 on 11.04 was fine. 

I am not back to the open source drivers on 11.10. I get dual monitor desktop extension automatically (no needto fiddle on setting). Video is very responsive, however my PC is very loud. The GPU fan does not spin off with the open source drievrs.

11.10 looks fine, but dual monitor support on 11.9 fails epically....

---

### Post by PhonicLynx on 2011-10-15
Try doing the "sudo aticonfig --initial --heads=2 --adapter=1 --xinerama=on" command.. reboot.. then edit the file /etc/X11/xorg.conf file and remove any of the screens that you don't need. as in.. mine had 4 heads... i didn't need all 4 only 2. If you've installed the restricted drivers you have no choice but to do a fresh install as it breaks it epicly!.. I just wiped and installed it from scratch and now it works beautifully.

---

### Post by ggx123qwe on 2011-10-15
> **PhonicLynx said:**
> Try doing the "sudo aticonfig --initial --heads=2 --adapter=1 --xinerama=on" command.. reboot.. then edit the file /etc/X11/xorg.conf file and remove any of the screens that you don't need. as in.. mine had 4 heads... i didn't need all 4 only 2. If you've installed the restricted drivers you have no choice but to do a fresh install as it breaks it epicly!.. I just wiped and installed it from scratch and now it works beautifully.

Did already 4 clean installs after 11.9 messes EVERYTHING....

this stopped being fun anymore....

---

### Post by ggx123qwe on 2011-10-19
> **ggx123qwe said:**
> Did already 4 clean installs after 11.9 messes EVERYTHING....

this stopped being fun anymore....


[http://blog.jvc26.org/2011/09/29/multimonitor-ubuntu-oneiric-fglrx](http://blog.jvc26.org/2011/09/29/multimonitor-ubuntu-oneiric-fglrx)

This post saved my life....pesky little bug in 11.10

Now I have no problems running 11.10 with multi monitor. I DID NOT use the 11.9 Catalyst (Post Release), but the 'ATI/AMD proprietary FGLRX graphics driver'

more info on 

[http://blog.jvc26.org/2011/09/29/multimonitor-ubuntu-oneiric-fglrx](http://blog.jvc26.org/2011/09/29/multimonitor-ubuntu-oneiric-fglrx)

---

### Post by PhonicLynx on 2011-10-19
Thsats exactly what I was saying though ... "THATS" what was crashing on me.. Thats how I would normally do it... The only way I could get it to work was to do it manually.

---

