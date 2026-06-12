---
title: "X crashes when playing video through totem or xine"
date: 2005-11-04
forum: General Help
---

### Post by PuleX on 2005-11-04
**Update: I found out that my issues are related to [the XV extension]("http://ubuntuforums.org/showpost.php?p=469033&postcount=8").**

Since a few days, I have trouble with playing movies e.d. through totem and xine. Both actually crash my X server, bringing me back to the Ubuntu login screen. Mplayer does work, but vlc crashes and brings down X too. 

Just so you know, I did try following these instructions again: [http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-music-and-movies](http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-music-and-movies) ...but xine / totem / vlc keep crashing. 

I couldn't find something useful in /var/log/Xorg.0.log , so I am now trying to find other ways to debug this problem. Can anybody point me in the right direction? 

Btw, I have a Radeon 9600 Pro, and am using the ATI fglrx drivers.

---

### Post by Teroedni on 2005-11-04
hmm are you from Norway :)
I am;)

Could you try with vesa or regular Ati(opensource) too see if you get the same problems then?

Have you installed w32 codecs

---

### Post by PuleX on 2005-11-04
I did install the w32 codecs. 
And I could try the other ati drivers. 

But it was all working perfectly a few weeks ago...

(and no, I'm actually from the Netherlands  :) )

---

### Post by Teroedni on 2005-11-04
Are you running 5.10 version?
Try to remove your videoplayers and install them again.

---

### Post by PuleX on 2005-11-04
Trying to remove totem is not such a good idea, since the entire ubuntu-desktop package is also uninstalled then. So I'll try uninstalling vlc and xine, and reinstalling those. 

Somehow, I dont believe that will solve this. They both use a different core to display video, so if both crash it should be something related to xorg. Then again, trying never hurt anyone...  :-)

---

### Post by PuleX on 2005-11-05
Well, that didn't work. 
I think I'll try out following the directions in this thread [1] to reinstall the ATI fglrx drivers, and I'll inspect my xorg.conf

[1] [http://ubuntuforums.org/showthread.php?t=75378&highlight=crashes](http://ubuntuforums.org/showthread.php?t=75378&highlight=crashes) 

But, why isn't there something useful to be found in the log files...
Am I not looking in the right place?

---

### Post by PuleX on 2005-11-05
I reinstalled the fglrx drivers etc. 
Still, xine and vlc crash and bring down X whenever I try to play a movie. Mplayer works. 

This is what I see in Xorg.0.log.old: 

```
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
AUDIT: Sat Nov  5 14:20:36 2005: 8794 X: client 2 rejected from local host
  Auth name: MIT-MAGIC-COOKIE-1 ID: -1
AUDIT: Sat Nov  5 14:20:36 2005: 8794 X: client 4 rejected from local host
  Auth name: MIT-MAGIC-COOKIE-1 ID: -1
AUDIT: Sat Nov  5 14:20:36 2005: 8794 X: client 3 rejected from local host
  Auth name: MIT-MAGIC-COOKIE-1 ID: -1
AUDIT: Sat Nov  5 14:20:36 2005: 8794 X: client 6 rejected from local host
  Auth name: MIT-MAGIC-COOKIE-1 ID: -1
AUDIT: Sat Nov  5 14:20:36 2005: 8794 X: client 5 rejected from local host
  Auth name: MIT-MAGIC-COOKIE-1 ID: -1
AUDIT: Sat Nov  5 14:20:36 2005: 8794 X: client 2 rejected from local host
  Auth name: MIT-MAGIC-COOKIE-1 ID: -1

   *** If unresolved symbols were reported above, they might not
   *** be the reason for the server aborting.

Fatal server error:
Caught signal 11.  Server aborting
``` 

The same log as above can be found in Xorg.0.log, but then without the 'Fatal server error'. So I suppose the MIT-MAGIC-COOKIE stuff is not related to the crash. 

Then there's an error in Xorg.0.log about my tv not being connected, and a long listing of drmOpen something: 

```
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card51
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card52
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card53
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card54
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
```

I cannot find a log for xine, or vlc. I'll look further...

---

### Post by PuleX on 2005-11-05
Ok, I have confirme that this is actually related to the Xv extension. Thanks to the FAQ on the Xine site: 
[http://xinehq.de/index.php/faq#XFREECRASH](http://xinehq.de/index.php/faq#XFREECRASH) 

I tried running xine with the XShm video output plugin from the command line: 
```
xine -V XShm
``` ...and that works like a charm! While 
```
xine -V Xv
``` ...indeed crashes X.

Now let's fix this.   :)

---

### Post by PuleX on 2005-11-05
xvinfo gives this output: 
```
$ xvinfo
X-Video Extension version 2.2
screen #0
  Adaptor #0: "ATI Radeon Video Overlay"
    number of ports: 1
    port base: 67
    operations supported: PutImage
    supported visuals:
      depth 24, visualID 0x23
      depth 24, visualID 0x24
      depth 24, visualID 0x25
      depth 24, visualID 0x26
      depth 24, visualID 0x27
      depth 24, visualID 0x28
      depth 24, visualID 0x29
      depth 24, visualID 0x2a
      depth 24, visualID 0x2b
      depth 24, visualID 0x2c
      depth 24, visualID 0x2d
      depth 24, visualID 0x2e
      depth 24, visualID 0x2f
      depth 24, visualID 0x30
      depth 24, visualID 0x31
      depth 24, visualID 0x32
    number of attributes: 12
      "XV_SET_DEFAULTS" (range 0 to 1)
              client settable attribute
      "XV_AUTOPAINT_COLORKEY" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 1)
      "XV_COLORKEY" (range 0 to -1)
              client settable attribute
              client gettable attribute (current value is 30)
      "XV_DOUBLE_BUFFER" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 1)
      "XV_BRIGHTNESS" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_CONTRAST" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_SATURATION" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_COLOR" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_HUE" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_RED_INTENSITY" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_GREEN_INTENSITY" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_BLUE_INTENSITY" (range -1000 to 1000)
              client settable attribute
              client gettable attribute (current value is 0)
    maximum XvImage size: 2048 x 2048
    Number of image formats: 4
      id: 0x32595559 (YUY2)
        guid: 59555932-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x59565955 (UYVY)
        guid: 55595659-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x32315659 (YV12)
        guid: 59563132-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x30323449 (I420)
        guid: 49343230-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
```

So it is installed and working. Question is, why does it crash....? 
When I go to System > Preferences > Multimedia Systems Selector > Video I can crash X by selecting one of the 2 XWindows options under Output and pressing the Test button.

---

### Post by Teroedni on 2005-11-05
Sorry i have no clue?
I hope someone else will be able to fix your broblem as im outta solution ,sorry:(

---

### Post by PuleX on 2005-11-05
[QUOTE=Teroedni]Sorry i have no clue?
I hope someone else will be able to fix your broblem as im outta solution ,sorry:([/QUOTE]

Well, thanks for your help anyway.   :) 
I now know where the problem lies, so eventually it will be fixed. It may be as simple as one change to a config file.

---

### Post by PuleX on 2005-11-05
I have not solved this issue yet. 
So, in case anyone may have a clue but needs some more info, my xorg.conf looks like this: 
```
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
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
	RgbPath		"/usr/X11R6/lib/X11/rgb"
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
EndSection

Section "Module"
	Load	"dbe"
	SubSection	"extmod"
		Option	"omit xfree86-dga"
	EndSubSection
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
#	Load	"extmod"
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
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9600 (R300 AP)"
	Driver		"fglrx"

  	# ### generic DRI settings ###
  	# === disable PnP Monitor  ===
	#Option		"NoDDC"
	# === disable/enable XAA/DRI ===
    	Option 		"no_accel" 	"no"
    	Option 		"no_dri"	"no"
	# === misc DRI settings ===
    	Option 		"mtrr" 		"off" # disable DRI mtrr mapper, driver has its own code for mtrr
	# ### FireGL DDX driver module specific settings ###
	# === Screen Management ===
    	Option 		"DesktopSetup" 	"0x00000000" 
    	Option 		"MonitorLayout"	"TMDS,STV"
#    	Option 		"IgnoreEDID"    "off"
    	Option 		"HSync2" 	"31.5"
    	Option 		"VRefresh2" 	"20 - 60"
    	Option 		"ScreenOverlap" "0" 
# === TV-out Management ===
#    	Option 		"NoTV" 		"no"
    	Option 		"TVFormat"      "PAL-B"     
    Option "TVStandard"                 "PAL-D"
    Option "TVHSizeAdj"                 "0"     
    Option "TVVSizeAdj"                 "-2"     
    Option "TVHPosAdj"                  "0"     
    Option "TVVPosAdj"                  "0"     
    Option "TVHStartAdj"                "0"     
    Option "TVColorAdj"                 "0"     
    	Option 		"GammaCorrectionI" 	"0x00000000"
    	Option 		"GammaCorrectionII"     "0x00000000"
# === OpenGL specific profiles/settings ===
    	Option 		"Capabilities"          "0x00000000"
    	Option 		"CapabilitiesEx"        "0x00000000"
# === Video Overlay for the Xv extension ===
    	Option 		"VideoOverlay"  "on"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
    	Option 		"OpenGLOverlay" "off"
# === Center Mode (Laptops only) ===
    	Option 		"CenterMode"                 "off"
# === Pseudo Color Visuals (8-bit visuals) ===
    	Option 		"PseudoColorVisuals"         "off"
# === QBS Management ===
    	Option 		"Stereo"                     "off"
    	Option 		"StereoSyncEnable"           "1"
# === FSAA Management ===
    	Option 		"FSAAEnable"                 "no"
    	Option 		"FSAAScale"                  "1"
    	Option 		"FSAADisableGamma"           "no"
    	Option 		"FSAACustomizeMSPos"         "no"
    	Option 		"FSAAMSPosX0"                "0.000000"
    	Option 		"FSAAMSPosY0"                "0.000000"
    	Option 		"FSAAMSPosX1"                "0.000000"
    	Option 		"FSAAMSPosY1"                "0.000000"
    	Option 		"FSAAMSPosX2"                "0.000000"
    	Option 		"FSAAMSPosY2"                "0.000000"
    	Option 		"FSAAMSPosX3"                "0.000000"
    	Option 		"FSAAMSPosY3"                "0.000000"
    	Option 		"FSAAMSPosX4"                "0.000000"
    	Option 		"FSAAMSPosY4"                "0.000000"
    	Option 		"FSAAMSPosX5"                "0.000000"
    	Option 		"FSAAMSPosY5"                "0.000000"
# === Misc Options ===
    	Option 		"UseFastTLS"                 "0"
    	Option 		"BlockSignalsOnLock"         "on"
    	Option 		"ForceGenericCPU"            "no"
	BusID		"PCI:3:0:0"
	Option 		"UseInternalAGPGART" 	"no"
	Screen 0
EndSection

Section "Device" 
	Identifier 	"Device[1]" 
	Driver 		"fglrx" 
	BusID 		"PCI:3:0:0" 	#adjust using 'lspci' or cat /proc/pci 
	Screen 1 
#	Option "TVOutFormat" 		"Composite" 	#or S-VIDEO etc 
	Option "TVStandard" 		"PAL-B" 	#or NTSC etc 
	Option "ConnectedMonitor" 	"TV" 
EndSection

Section "Monitor"
	Identifier	"A150X1"    
	HorizSync   	28-65
    	VertRefresh 	56-78
	Option		"DPMS"
EndSection

Section "Monitor" 
	Identifier 	"TV"  
	HorizSync 	60 
	VertRefresh 	30-150 
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"ATI Technologies, Inc. Radeon 9600 (R300 AP)"
	Monitor		"A150X1"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection


Section "Screen" 
	Identifier 	"Screen1" 
	Device 		"Device[1]" 
	Monitor 	"TV" 
	DefaultDepth 	24 
	SubSection 	"Display" 
		Depth 		24 
		Modes 		"640x480"
		ViewPort 	0 0 	# initial origin if mode is smaller than desktop 
	EndSubSection 
EndSection


Section "ServerLayout"
    	Identifier  	"Server Layout"
	Screen 		"Screen0"
	Screen 		"Screen1" RightOf "Screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection
``` 

Furthermore: ```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)
```

---

### Post by PuleX on 2005-11-06
After quite some searching I found someone who has similar issues [1]. 
According to that support thread [2], Xv crashes X.org only when the secondary display is configured in xorg.conf **but** is not connected.  

[1] [http://www.stanchina.net/~flavio/debian/fglrx-archive/msg00838.html](http://www.stanchina.net/~flavio/debian/fglrx-archive/msg00838.html) 
[2] [http://www.stanchina.net/~flavio/debian/fglrx-archive/msg00900.html](http://www.stanchina.net/~flavio/debian/fglrx-archive/msg00900.html) 

I just checked it, and it's true. When the tv is connected and turned on when I start X, all video players work as intended. This is fun...

---

### Post by deaddy on 2005-11-24
I have exactly the same problem with you. And i still can't find a solution for it.
I am using Ubuntu 5.10
Ati radeon 9550 video card.

---

### Post by deaddy on 2005-11-24
I got rid of that error message by using ati as a driver in xorg.conf. 
But this thing has very low 3D performance. Any other solution? :confused:

---

### Post by punkr0x on 2005-11-26
What does the xv engine do?  I was having the same problems, totem crashed X every time I tried to open a music file.  I was able to fix the problem by turning off xv.

---

### Post by akvik on 2005-12-04
I have the excact same problem, and it's getting on my nerves that X crashes everytime I open a video file without the TV connected. Is there a way to reinstall xv, or configure it?

---

### Post by jamesrw on 2005-12-11
same issue here... still working on it though.

---

### Post by jamesrw on 2005-12-13
fixed the problem so that xine could start correctly by opening xine from terminal with:

xine -V XShm

then in xine's application settings I changed the driver from auto to xshm.

---

### Post by nsasch on 2005-12-17
I have a similar problem, untill you mentioned the TV part.
I use Xorg with an ATI Radeon 7500 card with two monitors.  Both are connected, and I use MergedFB to get them to work.
The most recent change I made to Xorg.conf was the addition of Load "dbe"
xine and totem and such work for my user, but another user on my system has this issue.
My options in Media Systems Selector is XWindows (No Xv).  I'm unsure of the other user's selection.
I removed Load "dbe" and it's working.

---

### Post by PuleX on 2006-05-08
FYI, there's a bug report on this issue (xv-overlay crashes xorg when dual head is configured but 2nd screen not attached) on the unofficial ATI linux drivers bugtracker: 
[http://ati.cchtml.com/show_bug.cgi?id=179](http://ati.cchtml.com/show_bug.cgi?id=179)

---

