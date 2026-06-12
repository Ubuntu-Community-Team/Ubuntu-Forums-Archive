---
title: "Wacom Graphire 4 Tablet with Breezy"
date: 2005-12-23
forum: Hardware &amp; Laptops
---

### Post by jTHEn on 2005-12-23
I'm sorry to post another thread on Wacom tablet thread since I know there are so many. However, I've been through them all and they haven't done me any good. I have Breezy installed and a brand new Wacom Graphire 4 tablet (USB). Without editting xorg.conf or changing anything, it works just like a mouse (allowing me to thus draw in GIMP and Inkscape, but not sensing any tilt or pressure differences). I tried using this [how-to]("http://ubuntuforums.org/showthread.php?t=25151") and editted xorg.conf accordingly (changing event4 to event1 since that's where sudo cat detected it). After restarting X, my tablet does not move the cursor onscreen at all anymore. I have made the appropriate adjustments to the input device configuration, and have made sure to change my mouse's device from /dev/input/mice to its own /dev/input/mouse1 to prevent it from conflicting as well.

Anyone who has gotten the Graphire 4 to work in Ubuntu or has some useful advice, please help! Thanks so much

---

### Post by twisted_steel on 2005-12-26
I just got one of these tablets for Christmas and have the same problem. I'm going to play around with some of the settings tomorrow and hopefully I'll have better luck.

EDIT:
I just came across this thread, which looks like it has some sample configurations: [http://ubuntuforums.org/showthread.php?t=84170](http://ubuntuforums.org/showthread.php?t=84170)

---

### Post by 23meg on 2005-12-26
Please post your xorg.conf file.

---

### Post by twisted_steel on 2005-12-26
I have the xorg driver and the wacom-tools package installed, and I can move the cursor around if I don't configure the tablet and let it get caught by /dev/input/mice. The /dev/input/wacom symlink is setup when I plug the tablet in (I think wacom-tools added some udev rules).

I've included my eraserhead and touchpad configurations in case that's screwing anything up.

```

# Onboard Thinkpad eraserhead and touchpad
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
#       Option          "Device"                "/dev/input/mice"
        Option          "Device"                "/dev/input/mouse2"
        Option          "Protocol"              "ImPS/2"
EndSection
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "on"
EndSection

# Wacom graphics tablet - Graphire4 in my case
Section "InputDevice"
        Identifier "cursor"
        Driver "wacom"
        Option "Device" "/dev/input/wacom"
        Option "Mode" "absolute"
        Option "Type" "cursor"
        Option "USB" "on"
EndSection

Section "InputDevice"
        Identifier "stylus"
        Driver "wacom"
        Option "Device" "/dev/input/wacom"
        Option "Type" "stylus"
        Option "Mode" "absolute"
        Option "USB" "on"
EndSection

Section "InputDevice"
        Identifier "eraser"
        Driver "wacom"
        Option "Device" "/dev/input/wacom"
        Option "Type" "eraser"
        Option "USB" "on"
EndSection

``` 
Then follows the graphics card and monitor information, which is followed by:

```

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
        InputDevice     "cursor"                "AlwaysCore"
        InputDevice     "stylus"                "AlwaysCore"
        InputDevice     "eraser"                "AlwaysCore"
EndSection

```

---

### Post by quietglow on 2005-12-26
I've also just picked up one of these tablets and am having no luck getting pressure sensitivity or the second tool (eraser etc) in the GIMP. I've also followed directions in other threads (xorg.conf mods) with no luck. I can post xorg.conf if needs be.

---

### Post by 23meg on 2005-12-26
Try making these changes in ServerLayout```
        InputDevice     "cursor" **"SendCoreEvents"**
        InputDevice     "stylus" **"SendCoreEvents"**
        InputDevice     "eraser" **"SendCoreEvents"**
```
And in GIMP make sure all your tablet devices are set to "Screen" mode in File / Preferences / Input Devices / Configure Extended Input Devices .

---

### Post by 23meg on 2005-12-26
For reference here are my settings for my tablet PC digitizer, working flawlessly with pressure sensitivity. For standalone tablets ignore my device settings and ForceDevice. ```

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"        "/dev/ttyS14"
    Option        "InputFashion" "Tablet"
    Option        "ForceDevice"    "ISDV4"
    Option        "Name" "GRAPHIRE / INTUOS (SERIAL)"
    Option        "SendCoreEvents" "on"
    Option        "Type"          "cursor"
    Option        "Mode"          "absolute" 
    Option        "Vendor" "WACOM"
    Option        "Speed"         "3.0"
    Option        "Threshold"     "1"
    Option        "Tilt"          "on"
    Option	     "Button2"	"3"
    #Option    "DebugLevel"    "10"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"        "/dev/ttyS14"
    Option        "Type"          "stylus"
    Option        "InputFashion" "Pen"
    Option        "SendCoreEvents" "on"
    Option        "Name"          "GRAPHIRE / INTUOS Stylus (SERIAL)"
    Option        "ForceDevice"    "ISDV4"
    Option        "Mode"          "absolute"
    Option        "Vendor" "WACOM"
    Option        "Tilt"          "on"
    Option        "TiltInvert"    "on"
    Option        "Threshold"     "1"
    Option	     "Button2"	"3"
   #Option    "DebugLevel"    "10"
EndSection

Section "InputDevice"
 Driver       "wacom"
 Identifier   "eraser"
 Option       "Device" "/dev/ttyS14"
 Option       "InputFashion" "Eraser"
 Option       "Name" "GRAPHIRE / INTUOS Eraser (SERIAL)"
 Option       "Type" "eraser"
 Option       "Mode" "absolute"
 Option       "Vendor" "WACOM"
 Option       "ForceDevice" "ISDV4" 
 Option        "SendCoreEvents" "on"
EndSection

```

---

### Post by quietglow on 2005-12-26
I just gave those settings a shot--still no dice. The tablet essentially acts like a mouse with no pressure and no second tool from flipping. Other than putting the cursor, stylus and eraser on "screen" in the gimp, I shouldn't have to do anything else with settings right? Thanks all!

---

### Post by quietglow on 2005-12-26
Messing around in the GIMP, I found the "device info" dialog, which is probably enabled when you have something other than the core pointer. Anyway, I've attached a screen shot of mine and you can see than the core input device is indicated and I cant see any way of selecting the other inputs (even though they are apparently recognized).

---

### Post by 23meg on 2005-12-26
[QUOTE=quietglow]Messing around in the GIMP, I found the "device info" dialog, which is probably enabled when you have something other than the core pointer. Anyway, I've attached a screen shot of mine and you can see than the core input device is indicated and I cant see any way of selecting the other inputs (even though they are apparently recognized).[/QUOTE]
Please post your current xorg.conf file.

---

### Post by quietglow on 2005-12-26
This post:  [http://ubuntuforums.org/showthread.php?t=71854&highlight=graphire+pressure](http://ubuntuforums.org/showthread.php?t=71854&highlight=graphire+pressure)

indicates that the graphire 4 isn't supported by the wacom driver included in the respositories. The good news is that the driver was updated a few days ago and one of the new features is support for this tablet. I'm gonna compile the driver and check it out...I'll report back about it.

---

### Post by 23meg on 2005-12-26
OK, since I don't have a Graphire I missed that. Make you sure you remove the driver package before compiling.

---

### Post by quietglow on 2005-12-26
Okay, I installed the new drivers and still can't get anything. This could be because my install was not correct:

I built the new driver without a problem. Following the directions at the site, I attempted to load the new driver from within the build directory, but got an error. When I checked the path that the HOWTO gave for the driver, I saw that my machine had a wacom.ko instead of a wacom.o as indicated. I went ahead and moved the original wacom.ko and copied in the one I'd just compiled. After a depmod -e, the module loaded fine. Still no change though: no second tool and no pressure sensitivity. 

FWIW, when I did a "locate wacom.o" as the driver HOWTO suggests, I got no results. What's the difference between the .o and .ko drivers?

Anyway, here's my xorg.conf for the heck of it:

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
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/event1"
  Option        "Type"          "cursor"
  Option        "USB"           "on"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/event1"
  Option        "Type"          "stylus"
  Option        "USB"           "on"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/event1"
  Option        "Type"          "eraser"
  Option        "USB"           "on"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
Option "AlwaysCore"
Option "Device" "/dev/input/event2"
Option "Protocol" "event"
Option "LeftEdge" "120"
Option "RightEdge" "830"
Option "TopEdge" "120"
Option "BottomEdge" "650"
Option "FingerLow" "14"
Option "FingerHigh" "15"
Option "MaxTapTime" "180"
Option "MaxTapMove" "110"
Option "ClickTime" "0"
Option "EmulateMidButtonTime" "75"
Option "VertScrollDelta" "10"
Option "HorizScrollDelta" "0"
Option "MinSpeed" "0.45"
Option "MaxSpeed" "0.75"
Option "AccelFactor" "0.020"
Option "EdgeMotionMinSpeed" "200"
Option "EdgeMotionMaxSpeed" "200"
Option "UpDownScrolling" "1"
Option "CircularScrolling" "0"
Option "CircScrollDelta" "0.1"
Option "CircScrollTrigger" "2"
Option "SHMConfig" "true"
Option "SHMConfig" "on"
EndSection

Section "Device"
	Identifier	"Intel Corporation Intel Default Card"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Intel Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
	InputDevice     "cursor"     "AlwaysCore"
        InputDevice     "stylus"     "AlwaysCore"
        InputDevice     "eraser"     "AlwaysCore"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by 23meg on 2005-12-26
Try my suggestion in post #6, and adding ```
    Option        "SendCoreEvents" "on"
``` to all tablet devices.

---

### Post by jTHEn on 2005-12-26
Are either of you with G4's getting the Wacom driver to get control of the tablet before usbhid?

According to the LinuxWacom Project's howto, more /proc/bus/usb/devices should show that the Wacom device's driver is "wacom," NOT "usbhid", as mine does, as you can see below:

```

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.01 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=056a ProdID=0016 Rev= 4.03
S:  Manufacturer=WACOM
S:  Product=CTE-640-U V4.0-3
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr= 40mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
```


The solution is supposedly [here]("http://linuxwacom.sourceforge.net/index.php/howto/buildhid6"), yet I followed the directions and still get the above output. 

Also, here is the appropriate parts of my xorg.conf, if it is helpful:


```
Section "InputDevice"
Driver "wacom"
Identifier "cursor"
Option "AlwaysCore" "on"
Option "Device" "/dev/input/wacom"
Option "InputFashion" "Tablet"
Option "Mode" "Absolute"
Option "Name" "GRAPHIRE / INTUOS (USB)"
Option "SendCoreEvents" "on"
Option "Tilt" "on"
Option "Type" "cursor"
Option "USB" "on"
Option "Vendor" "WACOM"
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "stylus"
Option "Device" "/dev/input/wacom"
Option "InputFashion" "Pen"
Option "Mode" "Absolute"
Option "Name" "GRAPHIRE / INTUOS Stylus (USB)"
Option "Protocol" "Auto"
Option "SendCoreEvents" "on"
Option "Tilt" "on"
Option "Type" "stylus"
Option "USB" "on"
Option "Vendor" "WACOM"
EndSection

Section "InputDevice"
Driver "wacom"
Identifier "eraser"
Option "Device" "/dev/input/wacom"
Option "InputFashion" "Eraser"
Option "Mode" "Absolute"
Option "Name" "GRAPHIRE / INTUOS Eraser (USB)"
Option "Protocol" "Auto"
Option "SendCoreEvents" "on"
Option "Tilt" "on"
Option "Type" "eraser"
Option "USB" "on"
Option "Vendor" "WACOM"
EndSection

[...]

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
        InputDevice     "cursor"     "AlwaysCore"
        InputDevice     "stylus"     "AlwaysCore"
        InputDevice     "eraser"     "AlwaysCore"
EndSection
```

The linuxwacom project page does seem to suggest that their driver should work with the Graphire 4, but perhaps they are mistaken? Or perhaps it is the kernel versions we are using? I'm preparing to add a Windows partition to my computer if I can't get this to work the way it's supposed to. :mad:

---

### Post by Zeddicus on 2005-12-26
> The linuxwacom project page does seem to suggest that their driver should work with the Graphire 4, but perhaps they are mistaken? Or perhaps it is the kernel versions we are using? I'm preparing to add a Windows partition to my computer if I can't get this to work the way it's supposed to. 

It works -- I'm just working out the bugs right now.

You can:

Compile the wacom driver -> rmmod usbhid -> insmod wacom.ko -> plug in Graphire (so that the wacom driver takes control of it instead of usbhid) -> modprobe usbhid.

And it "works"... but it's crash-prone for me.

Xorg logs show a ton of:
```
Error reading wacom device : Success
```

Before it dies.

For *me* compiling a new usbhid didn't work well -- it killed my Synaptics Touchpad, which is just unacceptable.

---

### Post by jTHEn on 2005-12-26
Hmm.. that doesn't appear to work for me...

what do you mean exactly by "compile the wacom driver?"

---

### Post by quietglow on 2005-12-26
I hate to complicate this but I'm also getting some nasty full system freezes if I unplug the tablet after loading the new wacom.ko. Just a note that you might want to do some backing up before messing with this alot.

---

### Post by quietglow on 2005-12-26
I did this:

> Compile the wacom driver -> rmmod usbhid -> insmod wacom.ko -> plug in Graphire (so that the wacom driver takes control of it instead of usbhid) -> modprobe usbhid.

And it dramatically changed the nature of my tablet. Now, the cursor only moves when the pen tip is on the tablet and there only click is a tap--no right click now. Still no pressure sensitivity nor second tool.

Is the driver borked?

Okay so maybe I need the new usbhid driver too...but this scares me:

> For *me* compiling a new usbhid didn't work well -- it killed my Synaptics Touchpad, which is just unacceptable.

I'm traveling right now so if I hose my system, I'm more or less gonna be without my laptop for a week...what did it do to the touchpad? Could you just slap the old driver back in?

---

### Post by 23meg on 2005-12-26
If you can't find a solution, I suggest you post to the linuxwacom mailing list, where your questions will get answered by the developers and/or people who know a lot about the drivers will help you.

---

### Post by twisted_steel on 2005-12-26
[quote=quietglow]I hate to complicate this but I'm also getting some nasty full system freezes if I unplug the tablet after loading the new wacom.ko. Just a note that you might want to do some backing up before messing with this alot.[/quote]

I noticed the same thing when testing various configurations with the driver that comes with breezy.  My laptop would be fine for a little while, then I could not use the mouse, keyboard, etc.

---

### Post by quietglow on 2005-12-26
Hmm...great. Yes, my symptoms have been really solid freezes--my laptop tends to announce these by having the fans come on full blast a la the new Apple g5's.

Okay, so this is the first tablet I've ever had. The correct operation is for the cursor to move under the pen when the pen isn't touching the tablet, right? The first button is the left mouse and the second is the right?

---

### Post by Zeddicus on 2005-12-26
> And it dramatically changed the nature of my tablet. Now, the cursor only moves when the pen tip is on the tablet and there only click is a tap--no right click now. Still no pressure sensitivity nor second tool.

GRR.

Mine is behaving this way as well now.  It *was* working quite well besides occasional lock-up, but... *something* changed.

 
> I'm traveling right now so if I hose my system, I'm more or less gonna be without my laptop for a week...what did it do to the touchpad? Could you just slap the old driver back in?

Sorry I wasn't clear -- while the new driver was loaded, the touchpad didn't respond.  Putting the old driver back restored it just fine... and now, after re-compiling both drivers, I'm getting different behavior -- the touchpad works fine with the new usbhid, but the G4 doesn't!  ARG!

---

### Post by quietglow on 2005-12-26
I like to mess with stuff (duh) but this is starting to look as if some more work needs to be done before its usable. Is there anything else missing besides pressure sensitivity and the eraser tool? (I know the first especially is pretty big)

---

### Post by twisted_steel on 2005-12-26
[quote=quietglow]Okay, so this is the first tablet I've ever had. The correct operation is for the cursor to move under the pen when the pen isn't touching the tablet, right? The first button is the left mouse and the second is the right?[/quote] 
You should be able to move the cursor around by hovering the pen over the tablet. In Windows XP, I want to say the bottom button (closer to the tip) was right click and the top one was left click. In Ubuntu, however, I have it set as a mouse at the moment, and the bottom button is a middle click and the top is a right click. I think this is only because of the mouse treatment.

I am curious what you get when running
```
sudo wacdump /dev/input/wacom
``` using whatever device you have set up. Using the Breezy driver, mine lists MODEL, VNDR, DEV, and SUB as Unknown. CLS is USB and ROM=4.0-3.

EDIT:
I should add that I don't have the device setup in xorg (just acts like a mouse), as I need to find a faster connection to download the kernel source before compiling the new driver.  Dialup takes forever :)

---

### Post by quietglow on 2005-12-26
See attached screenshot...is that the output from the tablet? The coordinates at the top shift when the cursor is moving of course.

---

### Post by twisted_steel on 2005-12-27
[quote=quietglow]See attached screenshot...[/quote] 
That's the output I've been getting. I was hoping it could autodetect the tablet information with the new driver. Help for wacdump lists supported devices, and Graphire 4 is not listed in mine, so I imagine that's why it cannot detect it with the Breezy drivers.

---

### Post by jTHEn on 2005-12-27
A couple notes:

I have already started a line of communication with the linuxwacom people on the discussion mailing list (it is the first one listed in the archives). It had started out over some even more basic issues. They haven't responded yet as far as the ones we are all having now. I recommend everyone with a G4 post replies with their current situation so when they get a chance, they have more clues to look at.

Also: For those who have not had a tablet before: A tablet generally runs in "absolute" mode, meaning that each spot on the drawing area corresponds to a spot on the screen. So, tapping the stylus in the upper right will ALWAYS move the cursor to the upper right of the screen. This is what makes drawing on a tablet so useful, you can draw in reference to the actual space you just drew in. With the G4, you can actually place a photo or paper under the plastic shell and trace over it (when it's working correctly). So far, nothing has gotten absolute mode working for me at all yet. In relative mode, if you ever moved the cursor away from your drawing path, you would be in a new spot when you went back to tracing again.

As far as wacdump, I must have done SOMETHING right (but with all I've messed around with, I don't know what it could be) since this is the output

```
wacdump v0.7.1

MODEL=Wacom Graphire4 6x8               ROM=4.0-3
CLS=USB  VNDR=Wacom  DEV=Graphire4  SUB=CTE_640




  BUTTON=+00000 (+00000 .. +00000)      RELWHEEL=+00000 (-00001 .. +00001)

    LEFT=             MIDDLE=              RIGHT=              EXTRA=
    SIDE=              TOUCH=             STYLUS=            STYLUS2=
     BT0=                BT1=                BT2=                BT3=
     BT4=                BT5=                BT6=                BT7=

```

It definitely notices what kind of tablet I have...although it doesn't seem to recognize any differences in tilt or pressure, just tapping, moving, and button presses.

---

### Post by quietglow on 2005-12-27
I appreciate you going through the effort of contacting the developers list. So has anyone acknowledged that there may be a problem with the g4 and the new driver? I haven't found anyone who has said theirs is working properly yet.

Edit:

Okay, I'm going back over the driver site and I see that the usbhid driver has a tendency to take over the tablet and not let the wacom driver work--which is a good thing at this point cause they wouldn't work at all without. So when we unload the usbhid and manually load the wacom.ko, then the tablet is *actually* running on the wacom driver, right? And we're getting similar incorrect behavior when doing that right?

---

### Post by Zeddicus on 2005-12-27
Okay, I got it working again. (without crashing this time! :))

Some niggles -- when I reboot I need to rmmod ubhid, plug it in, modprobe usbhid again, then restart X... I guess I need to figure out how to get wacom.ko to load *before* usbhid.  Entering wacom into /etc/modules didn't do it. :/  After that, it works like a champ (absolute positioning, pressure sensitivity, gimp/krita working perfect).

All I did was follow the HOWTO here: 

[http://linuxwacom.sourceforge.net/index.php/howto/main](http://linuxwacom.sourceforge.net/index.php/howto/main)

, step by step.

If someone wants/needs, I can post exactly what I did here, but like I said -- it amounts to carefully following the instructions there.

That said -- the drivers *do* work... there just seems to be some amount of voodoo involved. ;)

---

### Post by quietglow on 2005-12-27
Did you have to compile and use the provided usbhid?

Could you post the relevant portions of your xorg.conf?

And thanks for the work!

---

### Post by jTHEn on 2005-12-27
Yes, please do list your steps...there are so many (what seems to be) superfluous ones in the how-to, I don't know what exactly needs to be done in our situation.

I THOUGHT I had done what it said...but alas it is still not working for me


Thanks so much!

---

### Post by Zeddicus on 2005-12-27
Well, if I'm going to do this, might as well do it right and start from the very beginning. :)

This should be able to be done with less steps (e.g. just configure all options at once... but this is what *worked* so it's what I'm posting)

I'm assuming an up to date 2.6.12-10-386 Ubuntu linux kernel.

First, install the build environment:
```
sudo apt-get install build-essential
sudo apt-get install linux-source-2.6.12
sudo apt-get install linux-kernel-headers
```

Now, I don't recall if installing linux-source creates untars the source in /usr/src (or creates an appropriate symlink), so...

```
cd /usr/src/
tar xvjf linux-source-2.6.12.tar.bz2
#I find this next line helpful for having things find the source, but it's not needed if you don't mind specifying where your kernel source is.
sudo ln -sf linux-source-2.6.12 linux
```

Now that that's set, we can start on the howto:

```
mkdir ~/wacom #or some other directory, just temp for compiling)
cd ~/wacom
wget http://voxel.dl.sourceforge.net/sourceforge/linuxwacom/linuxwacom-0.7.2.tar.bz2
tar xvjf linuxwacom-0.7.2.tar.bz2
cd linuxwacom-0.7.2
```

Configure the kernel driver (wacom.ko) for compilation:

```
./configure --enable-wacom
```

After spitting out everything, you should end up with:

```
  BUILD ENVIRONMENT:
architecture - i686
[b]linux kernel - yes 2.6.11
kernel - yes /usr/src/linux[/b]

BUILD OPTIONS:
**wacom.o - yes**
```

Bolded are the important to look for.  If the linux kernel doesn't show 2.6.11 (if you're using 2.6.12... that's what it should be) and kernel as /usr/src/linux, you need to point configure to your kernel source directory with --with-kernel=/directory/with/source

Next, compile and load the driver.

```
make
cd src/2.6.11
sudo rmmod wacom
sudo insmod ./wacom
```

Not necessary, but nice for a sanity check -- run "dmesg", and look at the last few lines.  You should see something along these lines:

```
[4294781.810000] /home/zed/compile/linuxwacom-0.7.2/src/2.6.11/hid-core.c: v2.0 - 2.6.11.3-pc-0.1:USB HID core driver
```

Where /home/zed/compile would be replaced by where you compiled the driver.

Next, backup the old kernel wacom.ko driver and install the new one:

```
sudo cp /lib/modules/2.6.12-10-386/kernel/drivers/usb/input/wacom.ko ./wacom.ko.backup
sudo cp ./wacom.ko /lib/modules/2.6.12-10-386/kernel/drivers/usb/input/wacom.ko
```

Next, we want to compile a new usbhid driver.

```
cd ~/wacom/linuxwacom-0.7.2
./configure --enable-hid

##Look for: 
#BUILD OPTIONS:
#            hid.o - yes

make
```

And install it, just like wacom.ko.

```
cd src/2.6.11
sudo cp /lib/modules/2.6.12-10-386/kernel/drivers/usb/input/usbhid.ko ./usbhid.ko.backup
sudo cp ./usbhid.ko /lib/modules/2.6.12-10-386/kernel/drivers/usb/input/usbhid.ko
```

Next **reboot**.

When you're back -- we should build a new wacdump.  The one included in Ubuntu won't recognize the G4, as far as I can tell.

```
cd ~/wacom/linuxwacom-0.7.2
./configure

# Look for:
#  BUILD OPTIONS:
#**            wacdump - yes**

make
sudo make install
```

This will install a new copy of wacdump in /usr/local/bin/wacdump.

Test the detection of the tablet:

```
sudo modprobe wacom
sudo rmmod usbhid
sudo modprobe usbhid ## I do this to be sure that the wacom driver takes control of the tablet -- you can check /proc/bus/usb/input/devices to be sure.
sudo /usr/local/bin/wacdump /dev/input/wacom
```

You should see something like this:

```
wacdump v0.7.1

MODEL=Wacom Graphire4 6x8               ROM=4.0-3
CLS=USB  VNDR=Wacom  DEV=Graphire4  SUB=CTE_640




TOOLTYPE=NONE                            IN_PROX=+00000 (+00000 .. +00000)
  BUTTON=+00000 (+00000 .. +00000)         POS_X=+00000 (+00000 .. +16704)
   POS_Y=+00000 (+00000 .. +12064)      DISTANCE=+00000 (+00000 .. +00032)
PRESSURE=+00000 (+00000 .. +00511)      ABSWHEEL=+00000 (+00000 .. +01023)
RELWHEEL=+00000 (-00001 .. +00001)

    LEFT=             MIDDLE=              RIGHT=              EXTRA=
    SIDE=              TOUCH=             STYLUS=            STYLUS2=
     BT0=                BT1=                BT2=                BT3=
     BT4=                BT5=                BT6=                BT7=

```

Next, I added these sections to my /etc/X11/xorg.conf

```
Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom"   # USB ONLY
  Option        "Type"          "stylus"
  Option        "USB"           "on"                  # USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/wacom"   # USB ONLY
  Option        "Type"          "eraser"
  Option        "USB"           "on"                  # USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/wacom"   # USB ONLY
  Option        "Type"          "cursor"
  Option        "USB"           "on"                  # USB ONLY
EndSection
```

```
Section "ServerLayout"
        InputDevice    "cursor"    "SendCoreEvents"
        InputDevice    "stylus"    "SendCoreEvents"
        InputDevice    "eraser"    "SendCoreEvents"
EndSection

```

Next, we need to install a new Xorg driver, backing the original up.

```
cd /usr/X11R6/lib/modules/input
cp ./wacom_drv.o ~/wacom/wacom_drv.o.backup
sudo cp ~/wacom/linuxwacom-0.7.2/prebuilt/wacom_drv.o ./wacom_drv.o
```

Next, restart X (ctrl-alt backspace works for my purposes :p)

The tablet *should* be working at this point.

You might want to add "wacom" to /etc/modules, but you'll still need to rmmod usbhid, modprobe usbhid, restart X to get the tablet recognized after a reboot.

It worked for me, I hope it can help *someone*.

Attached is my xorg.conf for your reference.

Good luck!

---

### Post by jTHEn on 2005-12-27
Whooooo!

Worked for me!

Shouldn't it be possible to enable the tablet on startup by some sort of script?


...I could be wrong, I'm not very skillful with such things

---

### Post by Zeddicus on 2005-12-27
> Shouldn't it be possible to enable the tablet on startup by some sort of script?

It should, but I'm looking to see if there's a 'right' way to do it before I suggest something. :)

---

### Post by quietglow on 2005-12-27
I'm up too...you certainly rock my friend.

I also got things working just fine w/o a new usbhid module (because I was trying things out, not because I was too lazy to compile it...honestly :-) but with the new xorg driver from the precompiled folder. Off to play with inkscape!

---

### Post by Zeddicus on 2005-12-27
> I also got things working just fine w/o a new usbhid module...

Yeah... fact is, if the usbhid driver was working right, the rmmod/modprobe ridiculousness wouldn't be needed... if there's a problem with the drivers, *that's* the only place I can see it being in.

---

### Post by twisted_steel on 2005-12-28
I have yet to test out the drivers, but I found that I had to change the symlink for /usr/src/linux to get the kernel driver to compile properly. In my case I installed *linux-headers-2.6.12-10-686* and changed my symlink with
```
cd /usr/src/
sudo ln -sf linux-headers-2.6.12-10-686 linux
```

---

### Post by quietglow on 2005-12-28
For anyone who may be thinking of trying this using a laptop, be aware that once the tablet is functioning properly, your suspend/hibernate functions are probably going to be something between dead and dangerous. 

When I try to suspend with the tablet attached I get lots of usbhid errors indicating it cannot sleep the tablet, and then the machine locks up. Trying to rmmod the drivers and removing the tablet doesn't seem to help much--still getting hard freezes.

Bottom line: before removing the tablet or sleeping your computer, make sure you have everything saved.

---

### Post by twisted_steel on 2005-12-29
Thanks Zeddicus - it works! I have absolute positioning, eraser, and pressure sensitivity working, the GIMP recognizes it, and I can still use it as a regular input device :). I didn't replace the usdhid driver yet, but only the kernel and xorg drivers.

Any idea if it's possible to modify my xorg configuration so I can still run X even without the tablet plugged in? I have a laptop and it's not exactly practical, however I could deal with copying config files and restarting X if I absolutely have to.

---

### Post by Zeddicus on 2005-12-29
> Bottom line: before removing the tablet or sleeping your computer, make sure you have everything saved.

I haven't exactly trusted suspending my laptop on any OS, so... yeah. ;)

> Any idea if it's possible to modify my xorg configuration so I can still run X even without the tablet plugged in?...

Odd... mine is working fine w/o the tablet plugged in.  Did you change your Corepointer settings beyond what I had?  (your main pointer is still set as /dev/input/mice, yes?)

(and it seems that my attached xorg.conf got mangled to all hell... I can repost it when I get home, if needed.)

---

### Post by twisted_steel on 2005-12-29
[quote=Zeddicus]Odd... mine is working fine w/o the tablet plugged in. Did you change your Corepointer settings beyond what I had? (your main pointer is still set as /dev/input/mice, yes?)[/quote] 
It looks like X is working even when it's not plugged in. Now I'm explicitly selecting /dev/input/event4 as the device, so maybe this had something to do with it.

I'm wondering how I am supposed to set up my build environment for compiling these drivers. I have /usr/src/linux pointing to /usr/src/linux-headers-2.6.12-10-686 and that allows me to compile the kernel driver, but not the hid driver. If I run ./configure --enable-hid, there are warnings about it not being able to find hid-core.c and hid.h in the kernel tree. I ran locate to see where they are, and hid-core is found in ```
/usr/src/linux-source-2.6.12/drivers/usb/input/hid-core.c
``` whereas hid.h is located in ```
/usr/src/linux-headers-2.6.12-10/include/config/usb/hid.h
and
/usr/src/linux-source-2.6.12/drivers/usb/input/hid.h
``` If I try to compile with linux-source specified as the location, it doesn't work because it cannot find version.h, which is located in the headers.

---

### Post by Zeddicus on 2005-12-29
Eep.  Yeah... that was one of the things I was a bit concerned about -- I've needed the kernel source a few times, and have done some things that might have been a bit different than stock...  but when building the usbhid driver, I always pointed to linux-source.

If you:

```
cd /usr/src/linux-source-2.6.12/
sudo make mrproper
cd ~/wacom/linuxwacom-0.7.2
./configure --with-kernel=/usr/src/linux-source-2.6.12 --enable-hid
```

Does that work?

---

### Post by twisted_steel on 2005-12-30
[quote=Zeddicus]Does that work?[/quote] 
I got the same sort of errors as before. I played around with it a bit and copied version.h, the kernel config file, and Module.symvers to the kernel source (which removed some of the initial config warnings), but that resulted in a whole mess of errors during make saying things like "storage size of ... isn't known" and "... is already defined."

---

### Post by philigran on 2005-12-30
[See next post]

---

### Post by philigran on 2005-12-30
This must be one of the most informative threads I found so far on Ubuntu's Wacom problem, yet...

I still can't get my tablet to work properly, and I'm writing here just to make sure that my problem really is that I'm trying to avoid recompiling the kernel before I choose to waste precious time by taking that risk.

Now, suppose that my Graphire 3 tablet works relatively fine, except that the scroll button is either inverted or simply jittering indecisively between both directions when, say, attempting to scroll a window under XFCE4.  A wacdump will reveal that a RELWHEEL value will decrease when scrolling up and decrease when scrolling down.  My stylus doesn't seem too reliable either, since the TOUCH value usually appears to go DOWN when I hover a few centimeters over the tablet.  Is that  problem due to a bad wacom.c or wacom.o that's compiled into the 2.6.12-10-386 kernel -- or something close?  My xorg.conf looks fine, compared with those posted here, but maybe I'm neglecting to set some obscure options?  Do please tell me that all I need to do is to set some stupid option somewhere!

Thanks all for your help and happy '06...

---

### Post by twisted_steel on 2006-01-02
[quote=twisted_steel]I got the same sort of errors as before ...[/quote] 
I was able to get usbhid to compile by copying the hid.h from one location in the kernel headers to another that mirrored the way the kernel source was set up.

```
cd /usr/src/linux-headers-2.6.12-10/
sudo cp include/config/usb/hid.h drivers/usb/input/
```

---

### Post by twisted_steel on 2006-01-02
[quote=philigran]Now, suppose that my Graphire 3 tablet works relatively fine, except that the scroll button is either inverted or simply jittering indecisively between both directions when, say, attempting to scroll a window under XFCE4. A wacdump will reveal that a RELWHEEL value will decrease when scrolling up and decrease when scrolling down. My stylus doesn't seem too reliable either, since the TOUCH value usually appears to go DOWN when I hover a few centimeters over the tablet. Is that problem due to a bad wacom.c or wacom.o that's compiled into the 2.6.12-10-386 kernel -- or something close? My xorg.conf looks fine, compared with those posted here, but maybe I'm neglecting to set some obscure options? Do please tell me that all I need to do is to set some stupid option somewhere![/quote] 
I would personally try the new driver if you have time, but you may want to contact the [linuxwacom mailing list]("http://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss") to see if they have any other advice. You could try posting the relevant portions of your xorg.conf here and someone may have a better idea than me :)

---

### Post by bulldog5 on 2006-01-17
UPDATE: gcc-3.4 and related components were not all installed...that fixed it.  The tablet works perfectly now.  The only issue seems to be shared by several people here...I have to go through the rmmod, plug it in, insmod, restart x exercise after a reboot.  I can live with that...

Thanks for a great forum!

****

I have tried to follow the directions to get my Graphire4 working...

I am running 5.10 with 2.6.12-10-k7-smp but nothing shows up with:
dmesg | grep wacom
and i get an error that there is no driver when I try:
rmmod wacom & insmod wacom

When I try to build the driver, I get things that I don't know how to correct...

***
*** WARNING:
*** Unable to compile wacom.o without kernel build environment
*** wacom.o will not be built
***
***
*** WARNING:
*** Unable to compile wacom_drv.{o,so} without XF86 build environment
*** or Xorg SDK.
*** wacom_drv.o will not be built
***

and this...

----------------------------------------
  BUILD ENVIRONMENT:
       architecture - i686
       linux kernel - yes 2.4
  module versioning - no
      kernel source - no
           Xorg SDK - no /usr/src/wacom/linuxwacom-0.7.2
          XSERVER64 - no
           dlloader - no
               XLib - yes /usr/X11R6/lib
                TCL - yes /usr/include/tcl8.4/
                 TK - yes /usr/include/tcl8.4/
            ncurses - yes

  BUILD OPTIONS:
            wacom.o - no
            wacdump - yes
             xidump - yes
        libwacomcfg - yes
         libwacomxi - yes
          xsetwacom - yes
              hid.o - no
         usbmouse.o - no
            evdev.o - no
         mousedev.o - no
            input.o - no
        tabletdev.o - no
       wacom_drv.so - no
        wacom_drv.o - no
----------------------------------------

I think I have the kernel source, headers, etc. installed correctly (although this is my first ubuntu install...).  The kernel shows up as 2.4 rather than 2.6.12 and even when I use the --with-kernel= option, it shows 2.4 and the kernel source still says no.

Any ideas as to where to go from here would be appreciated!

Thanks,

---

