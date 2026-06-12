---
title: "Another ATI screen resolution question *sigh*"
date: 2006-12-30
forum: Hardware &amp; Laptops
---

### Post by spykecub on 2006-12-30
I think I can oficially say that I have read every last thread on this forum relation to ATI cards and screen resolutions! But still, ready to pull my hair out on this one...

I'm running edgy using an ATI radeon 9550. 
```
:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9550 Generic
OpenGL version string: 2.0.6011 (8.28.8)
```
I installed my ATI driver using the "install from repositories" instructions from [here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-02330ccb580b6a9411d32bf617cc5a82116ba6b9"). Works great. Sorta.

using the wonderful little "screen resolution" took for gnome under system-preferences I get a nice resolution of 1280x1024. Pretty nice, especially considering my xorg.conf makes *no* mention of that resolution!! :D 

But still, greedy little me would love to get a higher resolution (1600x1200 would be nice).

My monitor is a [Mirai 19 inch]("http://www.mirai.eu/Uk/ProductDetails&product_id=29&cat_id=39") - cheap, yeah - but it looks nice on my desk :cool: 

Here's my xorg.conf
```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "dk"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "C15-2"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 AS [Radeon 9600]"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV350 AS [Radeon 9600]"
	Monitor    "C15-2"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "0"
EndSection

```

I've tried doing a sudo dpkg-reconfigure xserver-xorg, but I end up getting a warning message at the end telling me that I'm modifying an already modified version of xorg, and when I restart I just get a wonderful "Out of Range" message from my monitor.

Restore backup, rinse, repeat.


So - any ideas what I can do to get a higher resolution, or am I a lost cause?

---

### Post by matthew on 2006-12-30
> **spykecub said:**
> 
I'm running edgy using an ATI radeon 9550. 
```
:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9550 Generic
OpenGL version string: 2.0.6011 (8.28.8)
```I installed my ATI driver using the "install from repositories" instructions from [here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-02330ccb580b6a9411d32bf617cc5a82116ba6b9"). Works great. Sorta.
Good news! We can make this work. For starters, good job--you already have the ATI drivers installed.

I am using the same version of the driver as you are so although our hardware is a little different (I have the ATI Mobility Radeon 9700 in my laptop) things are close enough for me to say I have some understanding. I have some comments interspersed among quotes...

Here we go.

> **spykecub said:**
> using the wonderful little "screen resolution" took for gnome under system-preferences I get a nice resolution of 1280x1024. Pretty nice, especially considering my xorg.conf makes *no* mention of that resolution!! :D 

But still, greedy little me would love to get a higher resolution (1600x1200 would be nice).

My monitor is a Mirai 19 inch - cheap, yeah - but it looks nice on my desk :cool: I'm not familiar with that specific monitor, but I think a simple modification of your xorg.conf will allow what you want. This is how we do that.

[COLOR=Red]EDIT: you added the link and I see the native resolution for this monitor is 1280x1024. You will not get anything better than that and this is the cause of the problems you mention below. I've changed what I have for the xorg.conf to compensate. If you have that resolution working then you are set up at the best possible for that piece of hardware and you can ignore the rest of this post.[/COLOR]

First, let's back up the existing one...I will make a note at the bottom of this post on how to revert to your current version of xorg.conf if you end up booting in text mode.

Open a terminal at Applications->Accessories->Terminal
Type this at the prompt. It will create a backup of your config file.```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```Next, open the original file and edit it. I'll tell you what to change below.
```
sudo gedit /etc/X11/xorg.conf
```Most of the file will be left alone. We will just change the following lines by adding the new resolutions you want to have available. Cut this and paste it in the proper place in the file.

```

Section "Screen"
    Identifier "Default Screen"
    Device     "ATI Technologies, Inc. RV350 AS [Radeon 9600]"
    Monitor    "C15-2"
    DefaultDepth     24
    SubSection "Display"
        Depth     1
        Modes    "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth     4
        Modes    "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth     8
        Modes    "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth     15
        Modes    "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth     16
        Modes    "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth     24
        Modes    "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

```> **spykecub said:**
> I've tried doing a sudo dpkg-reconfigure xserver-xorg, but I end up getting a warning message at the end telling me that I'm modifying an already modified version of xorg, and when I restart I just get a wonderful "Out of Range" message from my monitor.

Restore backup, rinse, repeat.

So - any ideas what I can do to get a higher resolution, or am I a lost cause?[COLOR=Red]EDIT: [/COLOR]Please bear in mind that your monitor has to be able to support these higher resolutions and [COLOR=Red]after[/COLOR] looking at your hardware manual I [COLOR=Red]can[/COLOR] tell you if it [COLOR=Red]only goes to 1280x1024 and trying anything larger would cause problems.[/COLOR]

In any case, save the modified file and we'll see if the monitor protests. We will now restart the x-server and see what happens. Write down or print the instructions below in case you have a problem and you will be able to undo all that we have just done and you will at least end up no worse off than you are now. Hit Ctrl+Alt+Backspace. If it makes you feel better you can reboot. Login again if it lets you and try to select a new resolution.

What to do if this fails and you're stuck at the command prompt...
login and type```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```and reboot.

---

### Post by spykecub on 2006-12-30
I actually found the link to my monitor specs AFTER making this post - and let me just say poop.

Oh well, that'll teach me not to buy cheap anymore!!! 



And by the way matthew - we may have run into a wall because of my crappy monitor, but your response ROCKS! It would be a great world to live in if everyone was so helpful and thorough! :)

---

### Post by matthew on 2006-12-30
> **spykecub said:**
> I actually found the link to my monitor specs AFTER making this post - and let me just say poop.

Oh well, that'll teach me not to buy cheap anymore!!! That's what I figured. It appeared while I was writing my response. It was helpful, though so I'm glad you added it. I hope the color looks good anyway. :)

> **spykecub said:**
>  And by the way matthew - we may have run into a wall because of my crappy monitor, but your response ROCKS! It would be a great world to live in if everyone was so helpful and thorough! :)Glad I could be of service.

---

