---
title: "how do i find out what video driver i'm using"
date: 2009-11-08
forum: Hardware
---

### Post by rhythmiccycle on 2009-11-08
The computer I have is used, and I just updated to ubuntu 9.10, and it won't go higher than a 800x600 resolution, 

I found this page:

[http://linuxandfriends.com/2009/02/13/change-screen-resolution-in-ubuntu-linux/](http://linuxandfriends.com/2009/02/13/change-screen-resolution-in-ubuntu-linux/)

and the line:
Driver    	"vboxvideo"
is added to xorg.conf

but I don't think I have the same driver as the person who wrote that page.

can I just write "vboxvideo" anyway?

if not, how do I find out what I'm supposed to write there?

---

### Post by scragar on 2009-11-08
vboxvideo is for virtual machines in Vbox, if you are running linux inside something like virtualbox.
If you want to know your graphics card using:
```
lspci | grep VGA
```
If you want to know your current graphics driver there is not much I can recommend other than checking to see what Xorg has decided to use:
```
grep 'Monitor name' /var/log/Xorg.0.log
```

---

### Post by rhythmiccycle on 2009-11-08
thanks for the reply,

it says this,

$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)


grep 'Monitor name' /var/log/Xorg.0.log, returns nothing.
Xorg.conf everything is "defult"

and the end of /var/log/Xorg.0.log says

```

(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): EDID for output VGA1
(II) intel(0): Not using default mode "640x350" (vrefresh out of range)
(II) intel(0): Not using default mode "640x400" (vrefresh out of range)
(II) intel(0): Not using default mode "720x400" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "640x480" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "800x600" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (hsync out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1024x768" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x960" (hsync out of range)
(II) intel(0): Not using default mode "1280x960" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x1024" (hsync out of range)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (hsync out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) intel(0): Not using default mode "1792x1344" (hsync out of range)
(II) intel(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) intel(0): Not using default mode "1856x1392" (hsync out of range)
(II) intel(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) intel(0): Not using default mode "1920x1440" (hsync out of range)
(II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) intel(0): Not using default mode "832x624" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (hsync out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1152x864" (vrefresh out of range)
(II) intel(0): Not using default mode "1360x768" (hsync out of range)
(II) intel(0): Not using default mode "1360x768" (hsync out of range)
(II) intel(0): Not using default mode "1400x1050" (hsync out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1440x900" (hsync out of range)
(II) intel(0): Not using default mode "1600x1024" (hsync out of range)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "1680x1050" (hsync out of range)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) intel(0): Not using default mode "1920x1080" (hsync out of range)
(II) intel(0): Not using default mode "1920x1200" (hsync out of range)
(II) intel(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) intel(0): Not using default mode "2048x1536" (hsync out of range)
(II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) intel(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) intel(0): Printing probed modes for output VGA1
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)

```

i really just what to get 1280x1024 working again.

 I'm so lost.

what do I do?

---

### Post by scragar on 2009-11-08
The driver you should be using is called 'intel', all lower case.

---

### Post by rhythmiccycle on 2009-11-08
thank you,

This is what I have in xorg.conf now:
```

Section "Device"
	Identifier	"Configured Video Device"
	Driver    	"intel"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth    24
   	
	SubSection "Display"
         	Depth     24
         	Modes     "1280x1024"
   	EndSubSection

EndSection

```

I rebooted, but its still in 800x600. I checked xrandr and display setting(GUI), but the 1280x1024 is not showing up. 

I don't know what to do next.

There is one other part that seems weird to me.
On the link I put on the first post of this thread, it has

Device    "VirtualBox graphics card"

under Section "Screen"

but I have,
 
Device		"Configured Video Device"

is this correct?

or maybe I should make it: "Integrated Graphics Controller"?
I'm not sure.

Or am I totally heading in the wrong direction?

---

### Post by scragar on 2009-11-08
OK, if that didn't work just reconfigure Xorg, see if that fixes it.
```

sudo dpkg-reconfigure xserver-xorg

```
Answer the questions as per this guide:
[http://www.freesoftwaremagazine.com/columns/how_to_fix_your_computers_graphics_with_dpkg-reconfigure](http://www.freesoftwaremagazine.com/columns/how_to_fix_your_computers_graphics_with_dpkg-reconfigure)

Your driver is "intel" like I said before, read the guide first, make sure you understand everything, if you have any questions ask before you decide to run that command, I wouldn't want you to mess anything up and make your situation worse.

---

### Post by rhythmiccycle on 2009-11-08
thank you for your help, scragar. I really need someone to get me through this.

> **scragar said:**
> , read the guide first, make sure you understand everything, if you have any questions ask before you decide to run that command, I wouldn't want you to mess anything up and make your situation worse.

I read the start of that page, but I'm not sure what my video card’s number is.

also could you please verify the other info.

this is what I have:

> 
You should already have installed your video card driver:
	I think this is done because it says “intel”

You should also know your monitor’s model number and manufacturer:
	model: VE175
	manufacturer: ViewSonic

your video card’s number and manufacturer:
	“00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics 	Controller (rev 04)”
	
	manufacturer: Intel
	??number: ??  82915G/GV/910GL OR rev 04


---

### Post by gradinaruvasile on 2009-11-08
> **rhythmiccycle said:**
> thank you,

This is what I have in xorg.conf now:
```

Section "Device"
	Identifier	"Configured Video Device"
	Driver    	"intel"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth    24
   	
	SubSection "Display"
         	Depth     24
         	Modes     "1280x1024"
   	EndSubSection

EndSection

```

I rebooted, but its still in 800x600. I checked xrandr and display setting(GUI), but the 1280x1024 is not showing up. 

I don't know what to do next.

There is one other part that seems weird to me.
On the link I put on the first post of this thread, it has

Device    "VirtualBox graphics card"

under Section "Screen"

but I have,
 
Device		"Configured Video Device"

is this correct?

or maybe I should make it: "Integrated Graphics Controller"?
I'm not sure.

Or am I totally heading in the wrong direction?

Did u transfer this installation from VirtualBox or something?

The configured video device is not a problem. its just an identifier, nothing to do with the actual model.

The command to reconfigure X server is:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Then reboot.

---

### Post by rhythmiccycle on 2009-11-08
> **gradinaruvasile said:**
> Did u transfer this installation from VirtualBox or something?


i didn't install or transfer anything (maybe thats the problem).

the code in xorg.conf I typed in myself based on what I was reading on a website.

every other version of ubuntu I used worked fine, but when I upgraded to 9.10, all of a sudden there was a problem. I don't understand whats going on. 

I just want to use, 1280x1024 again. 

> **gradinaruvasile said:**
> 
The configured video device is not a problem. its just an identifier, nothing to do with the actual model.

The command to reconfigure X server is:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Then reboot.

I typed that code in and then rebooted, but there seems to be no effect, i'm still in 800x600, and there is no option to get bigger in the display settings.

---

### Post by scragar on 2009-11-14
You could try forcing it, but if it fails things could be made worse.

```

xrandr -s 1280x1024

```

---

### Post by rhythmiccycle on 2009-11-15
I got it working, posted it on this thread:
[http://ubuntuforums.org/showthread.php?t=1321224](http://ubuntuforums.org/showthread.php?t=1321224)

---

