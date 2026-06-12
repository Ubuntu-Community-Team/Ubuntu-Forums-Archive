---
title: "Touchscreen"
date: 2006-07-14
forum: Hardware &amp; Laptops
---

### Post by Amt0571 on 2006-07-14
Hello,

I've been searching for a way to calibrate an LG 1510BF touchscreen and have not found any way to make it work with Ubuntu (or any other distro).

I have found drivers for Elo, Fujitsu, and some other touchscreensm but not for LG ones.

Can anyone help me to avoid having to install Windows?

Thanks

---

### Post by handy on 2006-07-15
It's a long shot, but have a look here:

**[http://www.via.com.tw/en/initiatives/spearhead/mini-itx/](http://www.via.com.tw/en/initiatives/spearhead/mini-itx/)**

Go down to near the very bottom of the page & you will find valuable linux links in the section with the following title:

**Enthusiast and Online Community Web Sites**

If it exists, you may very well get connected with what you want through these linux & hardware enthusiast groups?

All the best!

---

### Post by Amt0571 on 2006-07-15
Thanks, I'll try looking for a solution there... the computer is for a museum, and instead of what they were told to buy, they bought this LG screen... so now I have to either solve this problem  or install Windows... which I don't want to.


Thanks!

---

### Post by handy on 2006-07-15
> **Amt0571 said:**
> Thanks, I'll try looking for a solution there... the computer is for a museum, and instead of what they were told to buy, they bought this LG screen... so now I have to either solve this problem  or install Windows... which I don't want to.


Thanks!

If a driver is available, I would think that the miniitx crowd is a good bet for success...

---

### Post by Amt0571 on 2006-07-16
I've found that the screen uses an ITM touchscreen panel, and it seems it's already using an ITM touchscreen driver. So I only need to know how to calibrate it now... any help?

Thanks

---

### Post by esav on 2006-08-06
Have you made any progress on getting the touchscreen to work?

I'm currently struggling with LG 1730SF, has ITM touch as well, kernel driver loads nicely, catting /dev/inputX produces output. But so far I have not found anything to get it to work in xorg. A few sites have said itm touch should work just by defining it as PS/2 mouse (nope, doesn't work with mine). Some sites said touchscreens are quite standard and should work with almost any touch driver for xorg, nope no luck, tried everything I found, closest one is usbtouch driver with which I can see the events from  the debug output, though the packets received are quite not what the driver expects, X&Y bounce like mad no matter where I touch.

I definately don't want to install windows on this comp... (home automation control)

---

### Post by esav on 2006-08-06
Found another driver [http://www.mivu.no/itmtouch/](http://www.mivu.no/itmtouch/) but no luck with that either. I still get clicks all over the screen even if I touch on one spot on the screen all the time..

Does anyone know what the heck are the kernel drivers supposed to do? What good are they for... surely don't make the device look like a PS/2 mouse or anything. Or does LG touchscreen have completely different controller even though it is manufactured by ITM?

---

### Post by jpdelport on 2006-08-15
Hi,

I've stumbled across this thread when also trying to get an LG L1730SF working under Debian.

I've managed to get it going, but had to change the itmtouch kernel driver. I used the evtouch xorg input module together with itmtouch.

Find the diff for itmtouch ( kernel 2.6.17.8 ) and an Xorg config snippet below:

---8<---

--- /usr/src/linux/drivers/usb/input/itmtouch.orig.c	2006-08-15 13:36:57.000000000 +0200
+++ /usr/src/linux/drivers/usb/input/itmtouch.c	2006-08-15 13:38:31.000000000 +0200
@@ -111,9 +111,9 @@
 	input_regs(dev, regs);
 
 	/* if pressure has been released, then don't report X/Y */
-	if (data[7] & 0x20) {
-		input_report_abs(dev, ABS_X, (data[0] & 0x1F) << 7 | (data[3] & 0x7F));
-		input_report_abs(dev, ABS_Y, (data[1] & 0x1F) << 7 | (data[4] & 0x7F));
+	if (~data[7] & 0x20) {
+		input_report_abs(dev, ABS_Y, (data[0] & 0x1F) << 7 | (data[3] & 0x7F));
+		input_report_abs(dev, ABS_X, 4096 - ((data[1] & 0x1F) << 7 | (data[4] & 0x7F)));
 	}
 
 	input_report_abs(dev, ABS_PRESSURE, (data[2] & 1) << 7 | (data[5] & 0x7F));

---8<---

Section "InputDevice"
    Identifier "touchscreen"
    Driver "evtouch"
    Option "Device" "/dev/input/event1"
    Option "DeviceName" "touchscreen"
    Option "MinX" "200"
    Option "MinY" "300"
    Option "MaxX" "3850"
    Option "MaxY" "3800"
    Option "ReportingMode" "Raw"
    Option "Emulate3Buttons"
    Option "Emulate3Timeout" "50"
    Option "SendCoreEvents"
EndSection

---8<---

cheers
jp

---

### Post by godzilla on 2006-08-23
I have a toshiba libretto 50M and I want to know if I can get installed my touchscreen under a ubuntu 2.6 kernel. Does this kernel recognize this kind of devices during install ? Thank you .

---

### Post by heion on 2006-09-30
I'm yet another owner of a L1730SF from LG, and I haven't been able to get mine to work which is frustrating. Have any of you found a working solution?

I can't even get proper output from /dev/input/eventX even though the usb drivers and usbtouchscreen (itm) driver is loaded and the screen is detected.

Help appreciated. :)

EDIT: For some weird reason it seems that compiling itmtouch.c and using itmtouch.ko was much better than using the unified usbtouchscreen.ko driver that's in the newer kernels. Using itmtouch.ko I'm actually getting output from /dev/input/eventX and am able to move the cursor about, albeit it just jumps randomly.

EDIT: Playing around with the calibration script from the evtouch driver and finally I seem to be getting somewhere. I can use the touchscreen properly now, albeit a bit inaccurately. Calibrating a bit more will fix that I hope. :)

---

### Post by gvozden on 2006-10-19
For Dapper XOrg:

[LIST=1]
[*]copy evtouch_drv.o to /usr/lib/xorg/modules/drivers
[*]change xorg.conf:
[LIST]
[*]add to "ServerLayout":
```

    InputDevice    "touchscreen"

```
[*]add:
```

Section "InputDevice"
    Identifier "touchscreen"
    Driver "evtouch"
    #Option "Calibrate" "1"
    Option "CorePointer"
    Option "Device" "/dev/input/itmtouch"
    Option "DeviceName" "touchscreen"
    Option "MinX" "250"
    Option "MinY" "289"
    Option "MaxX" "3894"
    Option "MaxY" "3799"
    Option "ReportingMode" "Raw"
    Option "Emulate3Buttons"
    Option "Emulate3Timeout" "50"
    Option "SendCoreEvents" "On"
EndSection

```
[/LIST]
[*]create file /etc/udev/rules.d/00-itmtouch.rules (change GROUP, to match your needs):
```

DRIVER="itmtouch", KERNEL="event[0-9]*", SYMLINK="input/itmtouch%e", GROUP="empiredogs", OWNER="root", MODE=0660

```
[*]patch itmtouch.c:  static void itmtouch_irq(struct urb *urb, struct pt_regs *regs)
```

    swapx = 0;
    swapy = 0;
    swapxy = 0;

        if (swapx)
                x = (data[1] & 0x1F) << 7 | (data[4] & 0x7F);
        else
                x = 4096 - ((data[1] & 0x1F) << 7 | (data[4] & 0x7F));

        if (swapy)
                y = 4096 - ((data[0] & 0x1F) << 7 | (data[3] & 0x7F));
        else
                y = (data[0] & 0x1F) << 7 | (data[3] & 0x7F);

        abs = (data[2] & 0x1) << 7 | (data[5] & 0x7F);

        /* Value is 0x80 when pressed and 0xA0 when released */
        button = !(data[7] & 0x20);

        input_regs(dev, regs);

        if (button) {
                if (swapxy) {
                        input_report_abs(dev, ABS_X, y);
                        input_report_abs(dev, ABS_Y, x);
                }
                else {
                        input_report_abs(dev, ABS_X, x);
                        input_report_abs(dev, ABS_Y, y);
                }
        }

        input_report_abs(dev, ABS_PRESSURE, abs);
        input_report_key(dev, BTN_TOUCH, button);

        /* If you are experiencing double clicks, turn off "input_sync(dev)". */
        input_sync(dev);


```
instead of
```

        input_regs(dev, regs);

        if (!(data[7] & 0x20)) {
                input_report_abs(dev, ABS_Y, (data[0] & 0x1F) << 7 | (data[3] & 0x7F));
                input_report_abs(dev, ABS_X, (data[1] & 0x1F) << 7 | (data[4] & 0x7F));
        }

        input_report_abs(dev, ABS_PRESSURE, (data[2] & 1) << 7 | (data[5] & 0x7F));
        input_report_key(dev, BTN_TOUCH, ~data[7] & 0x20);
        input_sync(dev);

```
[*] make calibration tool. Go to evtouch source dir:
```

xmkmf
make ev_calibrate

```

You can also use [http://linux.chapter7.ch/touchkit/calibrator.c](http://linux.chapter7.ch/touchkit/calibrator.c) program for callibration, it works for any input driver.
[*] READ THE MANUAL for calibration
[/LIST]

---

### Post by bpm0 on 2006-12-15
Hi,
I have an LG L1730SF touch screen, use usbtouchscreen driver as included in kernel 2.6.19 and evtouch driver for Xorg.
I can move touchscreen cursor, but the screen does not provide valid x and y values. I have try to calibrate it with evtouch calibrate program, but I have not resolve this problem.
I have correctly set Xorg config file.

What are the values in Xorg/XFree config file for MinX, MinY, x0, ...

Thanks

---

### Post by trantako on 2007-04-01
I bought an LG L1730SF touch screen a couple of days ago. It took a lot of work to get it working on Ubuntu Dapper Drake 6.06! This thread helped a lot in the process, but did not provide all the information I needed, so I created a web page describing what I needed to do. Here's the link, hope it helps: [http://www.rantakokko.net/node/43]("http://www.rantakokko.net/node/43")

---

### Post by Gfiles on 2007-09-22
Hi Everyone,

I have also been battling with the L1730S monitor.

I have it working fine using this site "http://www.conan.de/lifebook".

There are some notes to add:

[LIST]
[*]Use the 0.8.6 version file when downloading. 0.8.7 has a bug.
[*]Before calibrating copy the "emty_driver" file to the root directory.
[*]use "sudo init 1" to shutdown the X Server.
[*]I can only get the Calibrated values to work in 1280x1024 resolution.
[/LIST]

My Xorg.conf has the following values:

Section "InputDevice"
    Identifier "touchscreen"
    Driver "evtouch"
    Option "Device" "/dev/input/event4"
    Option "DeviceName" "touchscreen"
    Option "MinX" "278"
    Option "MinY" "289"
    Option "MaxX" "3890"
    Option "MaxY" "3899"
    Option "ReportingMode" "Raw"
    Option "Emulate3Buttons"
    Option "Emulate3Timeout" "50"
    Option "SendCoreEvents" "On"
    Option "SwapY" "1"
    Option "Rotate" "cw"
EndSection

My only Problem now is to get the touchscreen to work at 1024x768 resolution.

Thanks,

---

### Post by sauronsmatrix on 2007-10-04
also, my xorg.conf
> # xorg.conf (xorg X Window System server configuration file)
#
# This help file was generated by dexconf, the Debian X Configuration tool, using
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

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Boardname	"nv"
	Busid		"PCI:0:5:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Modelname	"Custom 1"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1400	1050
		Modes		"1280x960@60"	"1280x1024@60"	"1152x864@75"	"1400x1050@60"	"1024x768@43"	"1024x768@60"	"1024x768@70"	"1024x768@75"	"1024x768@85"	"832x624@75"	"800x600@60"	"800x600@85"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@85"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"nv"
	Busid		"PCI:0:5:0"
	Driver		"nvidia"
	Screen	1
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"
	EndSubSection
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"uk"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	#Option		"Device"		"/dev/input/mouse0"
	Option		"Protocol"		"ImPS/2"
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

Section "InputDevice"
	Identifier	"Touchscreen"
	Driver		"evtouch"
	#Driver		"evdev"
	Option		"Device"		"/dev/input/evtouch_event"
	Option		"DeviceName"		"touchscreen"
	Option		"MinX"			"40"
	Option		"MinY"			"90"
	Option		"MaxX"			"4015"
	Option		"MaxY"			"4000"
	#Option 	"TapTimer" 		"0"
	#Option 	"LongTouchTimer" 	"250"
	Option 		"ReportingMode" 	"Raw"
	Option 		"SendCoreEvents" 	"On"	
	#Option		"Calibrate"		"1"
EndSection

Section "Device"
	Identifier	"NVIDIA"
	Driver		"nvidia"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"		"True"
	Option		"RenderAccel"		"True"
	Option		"AllowGLXWithComposite"	"True"
	Option		"DRI"			"True"
	Option		"Coolbits"		"1"
	Option		"HWCursor"		"True"
	Option		"BackingStore"		"On"
EndSection

Section "Monitor"
	Identifier	"LCD"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA"
	Monitor		"LCD"
	Defaultdepth	24
	Option		"RandRRotation" 	"on"
	SubSection "Display"
		Depth	24
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  	Screen 		"Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
	Inputdevice	"Touchscreen"		"CorePointer"
EndSection

and, this line:
Option		"Device"		"/dev/input/evtouch_event"

I looked, and there is no file /dev/input/evtouch_event there.

---

### Post by .neo on 2008-01-31
Option "Device" "/dev/input/evtouch_event" file should appear after you make udev rules changes, I guess!?

I too am having trouble in trying to perform just that one thing. No matter how or where I write the udev rule there's /dev/input/itmtouch file appearing?! Should I create the file myself beforehand?! Or maybe should I write the rule some other way then it said in the one post above, just by creating 00-itmtouch.rules faile with this only one line:

```

DRIVER="itmtouch", KERNEL="event[0-9]*", SYMLINK="input/itmtouch%e",  OWNER="root", MODE=0660

```


Plz help, I'm using Ubuntu 7.10 (Gutsy). BTW, the touchscreen works when I use /dedv/input/eventX (but number X changes after reboot) in the xorg.conf...

P.S.
To compile itmtouch.c in Gutsy (desktop-generic & not server) you'll need to comment out the .owner field in the itmtouch_driver struct.

---

