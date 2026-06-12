---
title: "screen resolution only 640x480"
date: 2005-07-15
forum: Hardware &amp; Laptops
---

### Post by intrigue on 2005-07-15
i installed ubuntu last night, and the installation was a breeze.  It looks really solid and functional, and i can't wait to get going using it.  during the X installation it prompted me for the screen resolutions i would like to run, and I disabled everything but 1024 (this is the native resolution of my laptop lcd). upon logging into gnome the screen resolution was only 640x480 with a 4" black border around it.  i went into the System>Preferences> Screen resolution  and the only choice is 640x480.  I thought it might not have detected and installed the right driver, so i did some searching and to my amazement found intel had a working linux driver for my card (intel 845GM) on their support website.  (Dell was no help) It was in rpm format, so i did some searching on that and found out i've gotta use the *alien -i package.rpm*   command.  I ran this as root without the x server running, and it seemed to have installed it fine.  I logged back into gnome and 640x480 was the only choice still.   

Im running a Dell Inspiron 1100.  

Is there some further configuration I need to be doing within gnome or grub?  I looked for a hardware manager to install the drivers like most OS's have and couldn't find one.  

As a possibly unrelated question, is there some way to increase the resolution outside of X?

What strikes me as odd, is that when i boot into the Ubuntu live cd and Knoppix the resolution is 1024, so i know there is a working driver out there.  Is there some way i could find out which driver these are loading and manually load it into my installation?  

Im sure its an easy newbie fix, but Ive looked in the forums and found nothing on installing this particular card, and don't know anything about configuring debian or ubuntu

thanks in advance for any help

---

### Post by stevenyu on 2005-07-15
Maunally edit the configuration files for the x server

---

### Post by evilghost on 2005-07-15
Here's some more detailed information:

```

sudo gedit /etc/X11/xorg.conf

```

Find the part of the xorg.conf that says Section "Screen", mine looks like this:

```

Section "Screen"
        Identifier      "Default Screen"
        Device          "NV6600GT"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024"
        EndSubSection
EndSection

```

You're going to be concerned with the "Modes" line.  Change this to the resolution you desire, save the file, and then hit CTRL-ALT-BACKSPACE to restart X.  As you can see by my xorg.conf snippet, I am running at 1280x1024.  You should now be running in the desired resolution.

Let me know if you have any other questions.

---

### Post by mikefeil on 2005-07-20
hi I have a satellite 4100xdvd laptop and have recently put ubuntu on it. I have done all the things you have said but I still have a resolution of 800x600 and this big black rim ?

is there any hope?

here is my xorg bits that relate to my monitor/resolution

Section "Device"
	Identifier	"Trident Microsystems Cyber 9525"
	Driver		"trident"
	BusID		"PCI:0:4:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Trident Microsystems Cyber 9525"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

---

### Post by mikefeil on 2005-07-20
is there anyway to stretch out the image on the monitor of a laptop like u would with a desktop monitor.

it seems like the resolution is okay, i just need to stretch the image out to get rid of this black 2in border

---

### Post by mikefeil on 2005-07-21
i just installed ubuntu on my mum's desktop and I got the exact same problem again.

it seems like i ahve tryed everything, there is just no way to force it?

---

### Post by Sam on 2005-07-21
Try with 16 bit colors:
```
Section "Screen"
        <snip />
        DefaultDepth    16
        SubSection "Display"
                Depth           16
                Modes           "1280x1024"
        EndSubSection
EndSection
```

---

### Post by gsmith on 2005-11-12
Check out this thread:

[http://www.ubuntuforums.org/showthread.php?t=48761](http://www.ubuntuforums.org/showthread.php?t=48761)

For the Dell Inspiron 1100 I believe manually specifying frequencies for your display in /etc/X11/xorg.conf will do the trick.  Example:

```
Section "Monitor"
Identifier "SDM-HS53"
HorizSync 28 - 48
VertRefresh 57 - 63
Option "DPMS"
EndSection
```

---

### Post by teaker1s on 2005-11-12
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbVariant"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV17 [GeForce4 MX 440] 128mb"
	Driver		"nv"
	BusID		"PCI:1:0:0"
	VideoRam	131072
EndSection

Section "Monitor"
	Identifier	"proview kx772ns monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 MX 440] 128mb"
	Monitor		"proview kx772ns monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by teaker1s on 2005-11-12
or if your brave 
sudo dpkg-reconfigure xserver-xorg
runs graphical wizard-be aware that a mistake will cause system not to boot and you will have to run from recovery mode and re run wizard

---

### Post by durfff on 2007-06-10
Bang on, nice one teaker!
Was looking for an ATI-specific thread to just upgrade resolution, I bumped on this thread and thought ah well, might give it a go

First tried to replace with this, as it's the same monitor number:

```
Section "Monitor"
Identifier "proview kx772ns monitor"
Option "DPMS"
HorizSync 30-70
VertRefresh 50-160
Modeline "1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection
```

And also upped possible resolutions by adding
```
"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768"
``` 
before each presented resolution...

Well like every journey it's not just a breeze it's trial and error, next time I reboot: eroor, can't load xorg.conf properly or something...
So booted with cd in safe graphics mode, logged on as root and edited xorg on my install with:
```
Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
EndSection
```

reboot and bam, working perfect ;)

I'm not too sure why the generic monitr works better as I have the same model number, a ProView 17inch if I'm right?

Anyways, working a treat, thanks for the post teaker!

Durfff

---

