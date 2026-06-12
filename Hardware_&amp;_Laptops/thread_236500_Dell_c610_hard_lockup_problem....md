---
title: "Dell c610 hard lockup problem..."
date: 2006-08-14
forum: Hardware &amp; Laptops
---

### Post by Papa-san on 2006-08-14
I have recently upgraded to Dapper. When using Breezy, I had no lockups... ever.
Now, I find that I get these complete system freezes that I cannot do anything with but power off. 

I am fairly convinced that it is a video driver issue, but have not been able to work it through. I am a real nOOb with linux, so don't really know enough to be 'safe' within the terminal. LOL

I followed the instructions in a wiki here: [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)
What happened was that upon re-boot, I had an error stating that "GDM" could not load due to improper configuration.

I managed to ```
sudo dpkg-reconfigure xserver-xorg
```
and I got back to where I was.

If anyone could help walk me through this, I would really appreciate it!

---

### Post by kaens on 2006-08-14
Are there any lines starting with (EE) in /var/log/Xorg.0.log ?

You can check really quick with this command:
```
 cat /var/log/Xorg.0.log | grep EE 
```

---

### Post by Papa-san on 2006-08-15
LOL...Um,,, one or two....
```
john@ubuntu:~$ cat /var/log/Xorg.0.log | grep EE
Current Operating System: Linux ubuntu 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) RADEON(0): Static buffer allocation failed.  Disabling DRI.
(EE) RADEON(0): At least 17325 kB of video memory needed at this resolution and depth.
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
john@ubuntu:~$
```

---

### Post by smelly_sox on 2006-08-15
It would seem that U R on the right track.
I have a C640 that works fine with Dapper.
This is **me**:
Open terminal
*sudo gedit /etc/X11/xorg.conf*

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	Option		"NoAccel"	"false"
	Option		"AGPMode"	"x4"
	Option		"AGPFastWrite"	"true"
	Option		"MonitorLayout"	"LVDS"
	Option		"EnablePageFlip""true"
	Option		"RenderAccel"	"true"
	Option		"AccelMethod"	"XAA"
	Option		"DynamicClocks" "true"
EndSection

Now to **U**:
Yours could be **very** similar except Identifier should be M6 not M7 & 7500 not 9000

Also, do you have a touchpad?
If not comment out the following in /etc/X11/xorg.conf
i.e. put a # at the start of each line. Like this
#Section "InputDevice"
#	Identifier	"Synaptics Touchpad"
#	Driver		"synaptics"
#	Option		"SendCoreEvents"	"true"
#	Option		"Device"		"/dev/psaux"
#	Option		"Protocol"		"auto-dev"
#	Option		"HorizScrollDelta"	"0"
#EndSection

It also appears U have no Wacom graphics tablet.
So comment out the sections containing
Driver "wacom"
Please comment whole section, as above, not simply one line containing wacom.

Just to be sure please post result of
*sudo lspci|grep VGA*
Output will determine if U should use radeon driver or not.

Regards

---

### Post by Papa-san on 2006-08-15
Thanks...
I do have a touchpad, so I'm not sure if I should do the remark out stuff or not...

(The touchpad works, however...? Double tapping only works when the mouse is unplugged)


```
john@ubuntu:~$ sudo lspci | grep VGA
Password:
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY

```How do I tell which driver I have loaded?  Is it the wrong one?
OK this is a portion of what I now have in /etc/X11/xorg.conf:

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "stylus"
#  Option        "Device"        "/dev/wacom"          # #Change to 
#                                                      # /dev/#input/event
#                                                      # for #USB
#  Option        "Type"          "stylus"
#  Option        "ForceDevice"   "ISDV4"               # #Tablet PC ONLY
#EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "eraser"
#  Option        "Device"        "/dev/wacom"          # #Change to 
#                                                      # /dev/#input/event
#                                                      # for #USB
#  Option        "Type"          "eraser"
#  Option        "ForceDevice"   "ISDV4"               # #Tablet PC ONLY
#EndSection

#Section "InputDevice"
#  Driver        "wacom"
# Identifier    "cursor"
#  Option        "Device"        "/dev/wacom"          # #Change to 
#                                                      # /dev/#input/event
#                                                      # for #USB
#  Option        "Type"          "cursor"
#  Option        "ForceDevice"   "ISDV4"               # #Tablet PC ONLY
#EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-70
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050"
	EndSubSection
EndSection
(The Radeon mobility 9000 is the default one in Dapper... Maybe this is why there are so many problems with the M6 LY cards?)

---

### Post by smelly_sox on 2006-08-15
Doin well, so again
*sudo gedit /etc/X11/xorg.conf*

Section "Device"
Identifier "ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
Driver **"ati"**
BusID "PCI:1:0:0"
EndSection

change ati to radeon
Also the resolution of your screen is set by Modes "1400x1050"
I have all mine set at Modes "1024x768"
I **suggest** you change them all.
save & reboot
Hope it all goes well.
If it does search ubuntu forums for enabling dri to gain 3D acceleration.
But for now C Ya.

---

### Post by Papa-san on 2006-08-15
Pickles... It put me back to the "Xserver" issue I had at the beginning of the thread... I did the ```
sudo dpkg-reconfigure xserver-xorg
``` thing again, and got it back to where it was... functions, but locks...

---

### Post by kaens on 2006-08-15
I think that's because it rewrote the config file? You shouldn't have needed to issue that command again, just restart X or reboot. Check /etc/X11/xorg.conf and see if the changes are still there.

Unless you mean that you rebooted (before issuing the reconfigure command) and still had the same problem.

---

### Post by Papa-san on 2006-08-15
Sorry... That's what I meant. When I re-booted, it came up with the xserver problem.

---

### Post by smelly_sox on 2006-08-16
Yeh sorry. My bad.
I forgot to mention U also need to comment out some more lines at the bottom of your xorg.conf file.

#	InputDevice     "stylus" "SendCoreEvents"
#	InputDevice     "cursor" "SendCoreEvents"
#	InputDevice     "eraser" "SendCoreEvents"

But don't despair, I've attached an xorg.conf file that should sort all of your problems out. As long as you are in Dapper 6.06! i.e Not Breezy or Warty, or Edgy.
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
# To update this file, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	Option		"NoAccel"	"false"
#	Option		"AGPMode"	"x4"
#	Option		"AGPFastWrite"	"true"
#	Option		"MonitorLayout"	"LVDS"
#	Option		"EnablePageFlip""true"
#	Option		"RenderAccel"	"true"
#	Option		"AccelMethod"	"XAA"
#	Option		"DynamicClocks" "true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
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

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

So U need to:
*sudo gedit /etc/X11/xorg.conf*
File / Save As /
*/etc/X11/xorg.conf.old*
File / New
copy all from above attachment & paste into new blank tab of gedit
File / Save As /
*/etc/X11/xorg.conf*
Yes you want to overwrite the existing file.

Reboot & post back
Regards

---

### Post by Papa-san on 2006-08-16
Well, after rebooting, I actually got back to my splash screen, and thence to my desktop! Woo Hoo..!\\:D/ 

The resolution is different, but if this ends the lock-ups, I am just plain happy..!:D 

I really don't know how much effort you went throught to do this for me, but the fact that you were willing to just adds to my confidence that dumping Microsoft was the right thing to do! 

Once again, Ubuntu, and it's community have shown me that there IS a better way!

I will also qualify this in case the freeze problem persists:

If It happens again, I will post again in this thread, so we can hopefully carry it through in case some other poor slob with one of these Dell Lattitude's runs into the same thing!

---

### Post by gustl87 on 2006-08-16
hello

i am using an ati m6 - and i got the same strange freezes.

but then i found this on the web^^:

[http://forums.gentoo.org/viewtopic-p-3237995.html](http://forums.gentoo.org/viewtopic-p-3237995.html)

and it worked after some modifications.
so it never freezed again (till now).

so you should use the driver called "ati" and if freezing continues, you might edit it as follows:

```
Section "Device"
        Identifier      "[PUT YOUR CURRENT CARD NAME HERE]"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
        #Option          "AGPMode" "4"
        #Option          "AGPSize" "16" # default: 8
        Option          "AGPFastWrite" "false" # MUST BE FALSE!!!
        Option          "SWcursor" "true" # MUST BE TRUE!!!
        #Option          "RingSize" "4"
        #Option          "BufferSize" "2"
        Option          "EnablePageFlip" "false" # necessary?
        Option          "EnableDepthMoves" "false" # MUST BE FALSE!!!
        #Option          "RenderAccel" "false"
        #Option          "AccelMethod" "XAA" # or XAA, EXA
        #Option          "DDCMode"
        #Option          "SubPixelOrder" "NONE"
        Option          "ColorTiling" "false" # MUST BE FALSE???
        #Option          "DynamicClocks" "true"
        #Option          "bioshotkeys"   "True"
        #Option          "XAANoOffscreenPixmaps" "true"
EndSection

```

#sorry for my bad english.

---

### Post by kaens on 2006-08-16
@gustl87 - there was no bad english in that post.

---

### Post by smelly_sox on 2006-08-17
I don't know the specifics of M6, my previous posts weres for Dell Latitude with M7. The Radeon Mobility M7 should **NOT** be run with Driver "ati", rather Driver "radeon". I'm guessing that the M6 was the previous model to the M7. So it would seem likely that Driver "radeon" should also be used. (As in the above post).

Papa-san: we can make your resolution higher if you like, but the native resolution of the LCD screen is 1024x768. Also you do not have 3D acceleration enabled yet.
```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	Option		"NoAccel"	"false"
#	Option		"AGPMode"	"x4"
#	Option		"AGPFastWrite"	"true"
#	Option		"MonitorLayout"	"LVDS"
#	Option		"EnablePageFlip""true"
#	Option		"RenderAccel"	"true"
#	Option		"AccelMethod"	"XAA"
#	Option		"DynamicClocks" "true"
EndSection
```
Next time you feel like playing around, remove the #'s from the start of the above lines, in xorg.conf. Reboot.

If you suffer no ill effects and want to really exploit your Radeon's capability, we'll find you some info on enabling fully blown 'dri' acceleration.

**Should** you run into any problems, i.e. get text console instead of graphics console, then follow:
Login as root
*nano /etc/X11/xorg.conf*
You should then be able to edit, i.e. replace the #'s, your xorg.conf. Once you have done that;
*Ctrl + X*,
*Y*,
*Enter*
*reboot*

Regards

---

### Post by Papa-san on 2006-08-17
Thanks Guys!

Yer Awesome!

---

