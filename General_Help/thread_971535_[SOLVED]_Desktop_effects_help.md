---
title: "[SOLVED] Desktop effects help"
date: 2008-11-05
forum: General Help
---

### Post by MojoMax on 2008-11-05
I have a Ati Xpress200 and compiz worked perfectly fine in 8.04 but when I upgraded to 8.10 It doesn't work

I've tried enabling the hardware drivers and it activates the driver but when I restart it says that the screen could not be found and compiz still doesn't work

I've tried envyNG but it won't start the terminal says I have to download envyng-qt I did that and installed the driver and when I restart the same thing happens my screen could not be found and becomes 800x600 while its 1440x900 and compiz doesn't work 

I've tried everything 

Please Help :D

---

### Post by eternalnewbee on 2008-11-05
1. Have you installed "compiz Manager"
2. Have you tried changing the resolution in: Main Menu > System > Preferences > Screen Resolution?
3. Have you tried enabling "Visual Effects" from Main Menu > System > Appearnce > Visual Effects?

---

### Post by MojoMax on 2008-11-05
> **eternalnewbee said:**
> 1. Have you installed "compiz Manager"
2. Have you tried changing the resolution in: Main Menu > System > Preferences > Screen Resolution?
3. Have you tried enabling "Visual Effects" from Main Menu > System > Appearnce > Visual Effects?

1. Yes
2. Yes, when I enable the driver there is only 800x600 and 640x480
3. Yes, desktop effects could not be enabled

It all worked fine in 8.04 :(

Thanks a lot for responding

---

### Post by eternalnewbee on 2008-11-05
Out of ideas. looked around a bit and this might be interesting for you.
[http://ubuntuforums.org/showthread.php?t=764633&highlight=ati+sticky](http://ubuntuforums.org/showthread.php?t=764633&highlight=ati+sticky)

---

### Post by MojoMax on 2008-11-05
> **eternalnewbee said:**
> Out of ideas. looked around a bit and this might be interesting for you.
[http://ubuntuforums.org/showthread.php?t=764633&highlight=ati+sticky](http://ubuntuforums.org/showthread.php?t=764633&highlight=ati+sticky)

I tried that too doesn't work :(

---

### Post by eternalnewbee on 2008-11-05
Patience is a virtue. Eventually someone will respond to your thread, who will be able to help you solve your problem.
In the meantime maybe you could retrace your steps. Double-check everything you did, including rebooting your system.
Through trial & error && with the help from the community, here on these forums, I managed to solve all my major problems and most my little problems. ( and solved some myself:D)

---

### Post by ellalan on 2008-11-05
Could you check in synaptics whether you have sccsm enabled. To get visual effects to set to custom you need to enable this sccsm. In synaptics, type simple-ccsm in search box. HTH.

---

### Post by MojoMax on 2008-11-05
> **ellalan said:**
> Could you check in synaptics whether you have sccsm enabled. To get visual effects to set to custom you need to enable this sccsm. In synaptics, type simple-ccsm in search box. HTH.

I downloaded it it doesn't change anything

---

### Post by saggitheman on 2008-11-05
.

---

### Post by MojoMax on 2008-11-06
> **saggitheman said:**
> Have you installed Fusion-icon. Make sure you start it!

Sorry what ?

---

### Post by eternalnewbee on 2008-11-06
Go to: Main Menu > Add/Remove Applications. In the search bar type compiz. A list will appear. Choose the one with the blue cube and apply.

---

### Post by eternalnewbee on 2008-11-06
As for your screen resolution: I just gave someone else, who also has problems with fixing the resolution, this link. Might be helpful to you too.
[http://www.ubuntu1501.com/2008/04/restart-x-server.html](http://www.ubuntu1501.com/2008/04/restart-x-server.html)

---

### Post by alwez_loner on 2008-11-06
> **saggitheman said:**
> Have you installed Fusion-icon. Make sure you start it!

What he meant to say id did you install Compiz fusion icon in Synaptic Manager? Well you have to install the compiz settings manager package, then the compiz fusion icon will appear.

You have to run the fusion icon in order to get the effects.

---

### Post by eternalnewbee on 2008-11-06
> You have to run the fusion icon in order to get the effects.
You can also do it by pressing ALT F2 and entering ```
compiz -- replace
``` or via: Main Menu > System > Preferences > CompizConfig Settings Manager.

---

### Post by MojoMax on 2008-11-06
> **eternalnewbee said:**
> As for your screen resolution: I just gave someone else, who also has problems with fixing the resolution, this link. Might be helpful to you too.
[http://www.ubuntu1501.com/2008/04/restart-x-server.html](http://www.ubuntu1501.com/2008/04/restart-x-server.html)

Yeah I knew about that but when I do that the driver disables so yeah thanks though :)

---

### Post by Kevbert on 2008-11-06
It may be worth running [[COLOR="Red"]compiz-check[/COLOR]]("http://forlong.blogage.de/entries/pages/Compiz-Check") as some drivers for ATI have been blacklisted due to a bug.

---

### Post by MojoMax on 2008-11-06
> **Kevbert said:**
> It may be worth running [[COLOR="Red"]compiz-check[/COLOR]]("http://forlong.blogage.de/entries/pages/Compiz-Check") as some drivers for ATI have been blacklisted due to a bug.

I did that already


Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RS600 [Radeon Xpress 1200 Series]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]

---

### Post by Kevbert on 2008-11-07
Please post your xorg.conf file.

---

### Post by Peter09 on 2008-11-07
Checking the Configuration your Video Driver:


post the output of the code below so that we can see which driver is active.
lshw -C display

---

### Post by MojoMax on 2008-11-07
> **Kevbert said:**
> Please post your xorg.conf file.

xorg.conf
```
# xorg.conf (X.Org X Window System server configuration file)
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

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"intl"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

```

sudo lshw -C display
```
*-display               
       description: VGA compatible controller
       product: RS600 [Radeon Xpress 1200 Series]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=fglrx_pci latency=64 module=fglrx

```

---

### Post by MojoMax on 2008-11-09
Bump :confused:

---

### Post by Kevbert on 2008-11-10
There seems to be a few problems with the 'fglrx' driver, compiz and Intrepid flying around at the moment. I've looked on the compiz forum and it looks like your best bet is to try either the 'ati' or 'radeon' drivers.
See this [[COLOR="Red"]link[/COLOR]]("http://forum.compiz-fusion.org/showthread.php?t=9821&highlight=compiz+intrepid+fglrx") for additional settings (see xorg.conf).  You may need to run compiz-check again as I believe there is a potential bug with one of these drivers, so it may be blacklisted, but compiz-check will give you a solution in getting round this.

---

### Post by MojoMax on 2008-11-10
> **Kevbert said:**
> There seems to be a few problems with the 'fglrx' driver, compiz and Intrepid flying around at the moment. I've looked on the compiz forum and it looks like your best bet is to try either the 'ati' or 'radeon' drivers.
See this [[COLOR="Red"]link[/COLOR]]("http://forum.compiz-fusion.org/showthread.php?t=9821&highlight=compiz+intrepid+fglrx") for additional settings (see xorg.conf).  You may need to run compiz-check again as I believe there is a potential bug with one of these drivers, so it may be blacklisted, but compiz-check will give you a solution in getting round this.

My xorg.conf changed to this after I disabled the driver

```
# xorg.conf (X.Org X Window System server configuration file)
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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
```

---

### Post by Kevbert on 2008-11-11
Under Device Section you need to add
```
Driver "ati"
```
and add a new section
```
Section "Module"
Load "glx"
EndSection
```
Reboot and then try compiz-check again.

---

### Post by MojoMax on 2008-11-11
> **Kevbert said:**
> Under Device Section you need to add
```
Driver "ati"
```
and add a new section
```
Section "Module"
Load "glx"
EndSection
```
Reboot and then try compiz-check again.

Ok I did that 



```
Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RS600 [Radeon Xpress 1200 Series]
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [[COLOR="Red"]FAIL[/COLOR]]
 Checking for non power of two support...          [[COLOR="Red"]FAIL[/COLOR]]
 Checking for composite extension...               [ [COLOR="Lime"]OK[/COLOR] ]
 Checking for FBConfig...                          [[COLOR="Red"]FAIL[/COLOR]]
 Checking for hardware/setup problems...           [[COLOR="Wheat"]SKIP[/COLOR]]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size 

```

---

### Post by MojoMax on 2008-11-12
Sorry Bump :confused:

---

### Post by Kevbert on 2008-11-12
Sorry I haven't got back to you sooner.  What I tried is a Xubuntu 8.10 USB drive on my laptop which has an ATI RV250/Radeon 9000 which uses the same drivers. My xorg.conf file is the same as yours after you disabled the fglrx driver.  When I first ran compiz-check it failed badly on virtually all tests. I set the number of workspaces in compiz manager to four and the desktop only showed two workspaces so I set that also to four via right-clicking and selecting properties. I then ran compiz-check again and everything passed !??!  Compiz now seems to work for me without making any changes to xorg.conf (it's still as per your previous post) and compiz-check says I'm using the radeon driver (there is no driver detailed in xorg.conf). It shouldn't work but does :confused::confused::confused:

---

### Post by MojoMax on 2008-11-13
> **Kevbert said:**
> Sorry I haven't got back to you sooner.  What I tried is a Xubuntu 8.10 USB drive on my laptop which has an ATI RV250/Radeon 9000 which uses the same drivers. My xorg.conf file is the same as yours after you disabled the fglrx driver.  When I first ran compiz-check it failed badly on virtually all tests. I set the number of workspaces in compiz manager to four and the desktop only showed two workspaces so I set that also to four via right-clicking and selecting properties. I then ran compiz-check again and everything passed !??!  Compiz now seems to work for me without making any changes to xorg.conf (it's still as per your previous post) and compiz-check says I'm using the radeon driver (there is no driver detailed in xorg.conf). It shouldn't work but does :confused::confused::confused:

I've tried that but it doesn't seem to work thanks a lot though :)

---

### Post by espmartin on 2008-11-13
same issue here as MojoMax

---

### Post by LostOverThere on 2008-11-13
Same issue here too.

However, after a system update, the Nvidia driver 91 appears (one of the "bad" ones in 8.10 but the "fix" has arrived) however when I click to activate it. It says its downloading and installing but once that's done, the driver hasn't been activated. If I click activate again the same process happens.

And Yes, I had an Xorg.conf file like you did earlier, though It set back with a reboot. So yay-ish.

---

### Post by Peter09 on 2008-11-13
Did you logout and in again?

---

### Post by MojoMax on 2008-11-13
> **Peter09 said:**
> Did you logout and in again?

Yes

---

### Post by MojoMax on 2008-11-15
Bump:confused:

EDIT: I got it I got Compiz to work again I tried a bunch things so I don't know which one exactly did the job but here is my xorg.conf

```

# xorg.conf (X.Org X Window System server configuration file)
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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"

   #Load   "GLcore" 
	Load  "bitmap"
	Load  "ddc"
	Load  "dbe"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
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
	BusID       "PCI:1:5:0"
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

Section "DRI"
	Group        0
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection

```

---

