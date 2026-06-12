---
title: "No input from recognised Wacom pen tablet"
date: 2006-11-25
forum: Hardware &amp; Laptops
---

### Post by finferflu on 2006-11-25
Hi all,
Since I've installed Edgy Eft I can't use my Wacom pen tablet anymore.
I've been following some tutorials, [this]("http://ubuntuforums.org/showthread.php?t=25151"), [this one]("https://help.ubuntu.com/community/Wacom"), [this one]("https://help.ubuntu.com/community/QuickAndDirtyWacomSolution") and [this one]("https://help.ubuntu.com/community/WacomTabletIssue"), but apart from the fact that they seem to refer to previous releases of Ubuntu, all I could follow did not work for me. 

For example:

```
$ dmesg | grep wacom
[17179595.008000] usbcore: registered new driver wacom
[17179595.008000] drivers/usb/input/wacom.c: v1.45:USB Wacom Graphire and Wacom Intuos tablet driver
```

It shows me that the pen tablet is recognised, I think.

I've installed the wacom-tools and ran the command wacdump and I got this:

```
MODEL=Wacom Volito2 4x5                 ROM=2.0-0
CLS=USB  VNDR=Wacom  DEV=Volito2  SUB=CTF-420-U




TOOLTYPE=NONE                            IN_PROX=+00000 (+00000 .. +00000)
  BUTTON=+00000 (+00000 .. +00000)         POS_X=+00000 (+00000 .. +05104)
   POS_Y=+00000 (+00000 .. +03712)      DISTANCE=+00000 (+00000 .. +00032)
PRESSURE=+00000 (+00000 .. +00511)      RELWHEEL=+00000 (-00001 .. +00001)

    LEFT=             MIDDLE=              RIGHT=              EXTRA=
    SIDE=              TOUCH=             STYLUS=            STYLUS2=
     BT0=                BT1=                BT2=                BT3=
     BT4=                BT5=                BT6=                BT7=

```

But when I move the pen, I can see no input. 
Then I tried to uninstall the wacom-tools, and tried to look for the pen tablet on /dev/input/event#, with the command **sudo cat /dev/input/event#** but no joy. I've also unplugged it and re-plugged it, so that a new event was created (event5), but still, no sign of input.

So my problem is not in xorg.conf, but somewhere else. 

I also want to point out that all this is happening after a clean install (I've kept my /home, since I had my partition mounted there, but I don't think it makes any difference). 

Anyone could please help me? I really need to work with my pen tablet.

Thanks a lot for your time!

---

### Post by aksdb on 2006-11-25
I have the exact same problem with my Volito2. So maybe it's a problem with the driver not correctly supporting this tablet.

---

### Post by finferflu on 2006-11-25
Well, you might be right, I've also got a Volito2, which used to work on Dapper... what a pity...

---

### Post by finferflu on 2006-11-26
Sorted!

The problem was a bug in Edgy Eft, [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/61662](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/61662)

What needs to be done is copying the attached file to /lib/modules/2.6.17-10-generic/kernel/drivers/usb/input/

but before doing that is always good to make a backup copy of wacom.ko

```
$ cd /lib/modules/2.6.17-10-generic/kernel/drivers/usb/input/
mv wacom.ko wacom.ko_backup
```

and then untar and copy the new wacom.ko into that folder:

```
$ tar -zxvf <your download folder>/wacom.ko.tar.gz
sudo cp <your download folder>/wacom.ko /lib/modules/2.6.17-10-generic/kernel/drivers/usb/input/
```

Then reboot your machine, and the pen tablet is recognised!


Hope it helps anyone with a Volito2 on Edgy!

---

### Post by aksdb on 2006-11-26
Thanks for the hint, it worked fine after compiling the module from the current sources :)

---

### Post by finferflu on 2006-11-26
I'm glad it helped! :)

---

### Post by frying_fish on 2006-12-01
It may also be worth noting that creating a udev rule for the device will prevent you having problems of it appearing at a different /dev/input/eventX each time, and you can set it to something like /dev/input/wacom, which would always be the tablet.

my rule is:
```
BUS=="usb", SYSFS{name}=="Wacom Volito2 4x5", KERNEL=="input/event[0-9]", SYMLINK=input/wacom

```

Hopefully that will help (maybe it is a little different for you tablet, but udevinfo can get a lot of the information you will want)

---

### Post by finferflu on 2006-12-01
I thought you just needed to install wacom-tools to sort that problem out. For me that was enough to let it always appear under /dev/input/wacom.

---

### Post by jay_knight on 2006-12-10
Hi there,

Worked my way through multiple 'solutions' but none worked. I'm on Edgy x386, with a Wacom Graphire2. It seems to work after a clean install but I have two issues:

1) Gimp says: "No Extended input devices"
2) Also, my pointer doesn't move all the way to the edge of the screen.

Kind of a newbie (recent XP-->Ubuntu switcher), so any help is greatly appreciated!

Here's my xorg.conf:

```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
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
	FontPath     "/usr/share/fonts/X11/misc"
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
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
	Option	    "XkbVariant" "alt-intl"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mouse2"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/event2"          
	Option	    "Type" "stylus"
	Option        "USB"           "on"      
	Option        "PressCurve" "0,0,100,100"
#	Option	    "ForceDevice" "ISDV4"               
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/event2"          
	Option	    "Type" "eraser"
	Option        "USB"           "on"      
#	Option	    "ForceDevice" "ISDV4"               
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/event2"         
	Option	    "Type" "cursor"
	Option        "USB"           "on"      
#	Option	    "ForceDevice" "ISDV4"           
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    28.0 - 84.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
	Driver      "fglrx"
	Option	    "MetaModes" "1680x1050"
	Option	    "CRT2Position" "clone"
	Option	    "MonitorLayout" "LVDS,CRT"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1680x1050"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1680x1050"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

```

---

### Post by finferflu on 2006-12-10
Have you followed the tutorials I've linked in my first post? Have you installed wacom-tools? Your pen tablet should work with no problems, as long as I know the issue was only with Volito2.

Also, the issues you mentioned seem to indicate that the issue is with configuration, rather than with the pen tablet itself. 

I can notice from your xorg.conf that you are not using wacom as device, but input2 and also, you have some more options enabled than me:

```
Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection
```

In theory you shouldn't edit much in xorg.conf to make your pen tablet work...

---

### Post by jay_knight on 2006-12-11
Thanks for the reply!

Yes, I followed the tutorials. And the pen works, but only as a mouse, that is: no pressure sensitivity, and not detected in the Gimp and Inkscape.

My hardware is detected:

jeroen@Icarus:~$ dmesg | grep wacom
[17179596.076000] usbcore: registered new driver wacom
[17179596.076000] /home/sheep/linuxwacom-0.7.5-2/src/2.6.16/wacom_sys.c: v1.46:USB Wacom Graphire and Wacom Intuos tablet driver

and:

jeroen@Icarus:~$ more /var/log/Xorg.0.log |grep wacom
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"

And then this might be strange:

jeroen@Icarus:~$ more /var/log/Xorg.0.log |grep tablet
(==) Wacom Unknown USB tablet speed=9600 maxX=5472 maxY=4448 maxZ=255 resX=2540 resY=2540 suppress=2 tilt=disabled

A Graphire2 should be detected right?
Oh yeah... I am running XGL/Beryl (which some reported might give trouble?)

Thanks! J.

---

### Post by finferflu on 2006-12-11
There you go! We found the problem! XGL and wacom don't go together. You have to either log in in a non-XGL session or uninstall XGL altogether. That's what I did. I know it's a shame, but I'm looking forward for a fix, maybe in the next Ubuntu release. 

Let me know how it goes.

Good luck!

---

### Post by jay_knight on 2006-12-11
Ha ok! thats it then... Too bad: I was kinda getting used to all the eye-candy ;-) 

Is there a way of using Beryl without XGL (with ATI X700)?

Anyways, thanks for your help... sleeps better, knowing its not my inability to get things running ;-)

---

### Post by finferflu on 2006-12-11
I know, it was very sad to leave Beryl. In fact, I've started a discussion about it, you can follow it here: [http://ubuntuforums.org/showthread.php?t=313115](http://ubuntuforums.org/showthread.php?t=313115)

Somebody has told me that s/he was able to run Beryl without XGL, but s/he's not told me how to do it...

---

### Post by jay_knight on 2006-12-11
Thanks! I'll tap into that one then.

---

### Post by adam_pretty on 2007-02-06
I've got a Volito2, which I never got properly working in Dapper (x86) ... just upgraded, hoping it might help sort it out, but now not even recognised. I've swapped the new compiled wacom.ko into /lib/modules/2.6.17-10-386/kernel/drivers/usb/input/ .. no joy.

```
grep -i wacom /var/log/messages | tail 
``` gives:

```
Feb  2 17:22:57 localhost kernel: [17179612.576000] usbcore: registered new driver wacom
Feb  2 17:22:57 localhost kernel: [17179612.580000] drivers/usb/input/wacom.c: v1.45:USB Wacom Graphire and Wacom Intuos tablet driver
Feb  5 09:42:02 localhost kernel: [17179608.240000] usbcore: registered new driver wacom
Feb  5 09:42:02 localhost kernel: [17179608.244000] drivers/usb/input/wacom.c: v1.45:USB Wacom Graphire and Wacom Intuos tablet driver
Feb  5 09:44:46 localhost kernel: [17179772.456000] input: Wacom Volito2 4x5 as /class/input/input3
Feb  6 10:29:59 localhost kernel: [17179589.436000] wacom: disagrees about version of symbol struct_module
Feb  6 10:30:06 localhost kernel: [17179607.904000] wacom: disagrees about version of symbol struct_module
```

If anyone's got any hints would be great ... as I'm starting to get RSI again from using a mouse!

---

### Post by adam_pretty on 2007-02-08
* bump *

---

### Post by finferflu on 2007-02-08
> **adam_pretty said:**
> I've got a Volito2, which I never got properly working in Dapper (x86) ... just upgraded, hoping it might help sort it out, but now not even recognised. I've swapped the new compiled wacom.ko into /lib/modules/2.6.17-10-386/kernel/drivers/usb/input/ .. no joy.

```
grep -i wacom /var/log/messages | tail 
``` gives:

```
Feb  2 17:22:57 localhost kernel: [17179612.576000] usbcore: registered new driver wacom
Feb  2 17:22:57 localhost kernel: [17179612.580000] drivers/usb/input/wacom.c: v1.45:USB Wacom Graphire and Wacom Intuos tablet driver
Feb  5 09:42:02 localhost kernel: [17179608.240000] usbcore: registered new driver wacom
Feb  5 09:42:02 localhost kernel: [17179608.244000] drivers/usb/input/wacom.c: v1.45:USB Wacom Graphire and Wacom Intuos tablet driver
Feb  5 09:44:46 localhost kernel: [17179772.456000] input: Wacom Volito2 4x5 as /class/input/input3
Feb  6 10:29:59 localhost kernel: [17179589.436000] wacom: disagrees about version of symbol struct_module
Feb  6 10:30:06 localhost kernel: [17179607.904000] wacom: disagrees about version of symbol struct_module
```

If anyone's got any hints would be great ... as I'm starting to get RSI again from using a mouse!


Hi, sorry, I had forgotten I had to answer to you...
Your problem is very weird, since your pen tablet did not work on Dapper either. It used to work for me. 
Also, I can see that somebody else has had your same problem: [https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/61662](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/61662)

I am not an expert, but you can try to post there, so there will be three people with the same issue, and somebody might give you an appropriate answer...

That's as far as I can go with my knowledge, I hope it helps a bit...

---

### Post by adam_pretty on 2007-02-08
No worries, just posted in that page.

Thanks

---

