---
title: "G-Pen F610 Wacom Tablet on Ubuntu 10.04 - Stops working after tablet buttons pressed"
date: 2011-04-22
forum: Hardware
---

### Post by Stord on 2011-04-22
I followed this link [http://ubuntuforums.org/showthread.php?p=9966110](http://ubuntuforums.org/showthread.php?p=9966110) and went to this link [http://ubuntuforums.org/showpost.php?p=9573142&postcount=1](http://ubuntuforums.org/showpost.php?p=9573142&postcount=1)

Initially my wacom tablet was barely working (im  using it with a regular laptop), so i followed the above instructions. Now, it works except for this  - whenever i press a button on the wacompen, the pen stops working. The cursor still moves when i move the pen, its just that nothing is drawn in gimp! I have also had this experience in xournal. This also means that i cant click any buttons on a gui , or anything. In order to get it working again, i have to unplug/plug in the tablet. 

Has anyone had this problem and if so is there any way to fix it?

My 70-wizardpen.conf is shown below:



```

Section "InputClass"
   Identifier "wizardpen"
  # MatchIsTablet "on"
   MatchDevicePath "/dev/input/event*"
 
   MatchProduct "WALTOP|Tablet"

#[CALIBRATION] This data was taken from wizard-calibrate tool.
    	Driver		"wizardpen"

	Option		"TopX"		"487"
	Option		"TopY"		"1577"
	Option		"BottomX"	"18058"
	Option		"BottomY"	"8940"

#[END CALIBRATION]

  
EndSection


Section "InputClass"
   Identifier "wizardpen ignore mouse dev"
   #MatchIsTablet "on"
   MatchProduct "WALTOP"
   MatchDevicePath "/dev/input/mouse*"
   Option "Ignore" "yes"
EndSection


#Section "InputClass" 
#Identifier "wizardpen ignore mouse dev" 
#MatchIsTablet "on" 
##MatchDevicePath "/dev/input/mouse*" 
#MatchVendor "UC-LOGIC|KYE Systems|Ace Cad" 
#Driver "" 
#EndSection
```

---

### Post by Favux on 2011-04-22
Hi Stord,

We need to do some quick diagnostics to get a feel for what's going on.  Run these two commands in a terminal and post the outputs:
```
lsusb
```
and
```
xinput list
```

---

### Post by Stord on 2011-04-23
lsusb


```
Bus 004 Device 005: ID 172f:0034 Waltop International Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b091 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

xinput list

```

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; WALTOP International Corp. Slim Tablet  	id=10	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; CNF7047                                 	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]

```

---

### Post by Favux on 2011-04-23
OK, lets see if list-props will tell us if it is on the WizardPen driver:
```
xinput list-props "WALTOP International Corp. Slim Tablet"
```

---

### Post by Stord on 2011-04-23
```
Device 'WALTOP International Corp. Slim Tablet':
	Device Enabled (121):	1
	Device Accel Profile (238):	0
	Device Accel Constant Deceleration (239):	1.000000
	Device Accel Adaptive Deceleration (241):	1.000000
	Device Accel Velocity Scaling (242):	10.000000

```

---

### Post by Favux on 2011-04-23
Actually I think that means it is on the WizardPen driver.  I think I've seen that output not showing the driver before when it's WizardPen.  The driver would be shown multiple times if it was say wacom or evdev etc.  I suppose to be sure we have to look at the Xorg.0.log.  Sorry.  It's at /var/log.  Since it's big compress it with a right click and Create Archives and the post it with Managing Attachments below.

We have to make sure we're dealing with the correct driver.  In other words that your matches in the 70-wizardpen.conf are working and putting your Waltop on the WizardPen driver.

---

### Post by Stord on 2011-04-23
Here it is!

---

### Post by Favux on 2011-04-23
Alright, it looks like it's on the WizardPen X driver and everything is good:
```
(II) config/udev: Adding input device WALTOP International Corp. Slim Tablet (/dev/input/event6)
(**) WALTOP International Corp. Slim Tablet: Applying InputClass "evdev pointer catchall"
(**) WALTOP International Corp. Slim Tablet: Applying InputClass "evdev keyboard catchall"
(**) WALTOP International Corp. Slim Tablet: Applying InputClass "evdev tablet catchall"
(**) WALTOP International Corp. Slim Tablet: Applying InputClass "wizardpen"
(II) LoadModule: "wizardpen"
(II) Loading /usr/lib/xorg/modules/input/wizardpen_drv.so
(II) Module wizardpen: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.7.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Option "Device" "/dev/input/event6"
(--) WALTOP International Corp. Slim Tablet: MaxX:-1 MaxY:5761679 MaxZ:1023
(--) WALTOP International Corp. Slim Tablet: aspect ratio:1.60:1
(**) WALTOP International Corp. Slim Tablet is in absolute mode
(II) WALTOP International Corp. Slim Tablet: ScreenX = 1366, ScreenY = 768
(**) WALTOP International Corp. Slim Tablet: TopX                   = 487
(**) WALTOP International Corp. Slim Tablet: TopY                   = 1577
(**) WALTOP International Corp. Slim Tablet: BottomX                = 18058
(**) WALTOP International Corp. Slim Tablet: BottomY                = 8940
(**) WALTOP International Corp. Slim Tablet: TopZ    (min pressure) = 0
(**) WALTOP International Corp. Slim Tablet: BottomZ (max pressure) = 1023
(**) WALTOP International Corp. Slim Tablet: always reports core events
(II) XINPUT: Adding extended input device "WALTOP International Corp. Slim Tablet" (type: WizardPen Tablet)
(II) WALTOP International Corp. Slim Tablet Increment: 1
(II) config/udev: Adding input device WALTOP International Corp. Slim Tablet (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
```
Just to be sure does your tablet have 1024 levels of pressure like it says or is it 512?

So the stylus button problem is a new one on me.  It could be a problem with the Waltop usb kernel driver.  Certainly it doesn't work right with the Wacom X driver in Maverick.  Both buttons give the same response even if you've set them different.  But that was fixed with Nikolai's kernel patches by the 2.6.37 kernel I think.  Lucid has 2.6.32, Marverick has 2.6.35, and Natty has 2.6.37.

Maybe we just need to set the button map with xinput.  Or possibly it has something to do with the Z threshold (minimum pressure level)?  What do you want to try?  There are two side buttons on the stylus, correct?

---

### Post by Stord on 2011-04-24
Maybe try the button map with xinput?

I just tried it on another computer which has ubuntu 10.10 - i get the same problem. 

Another observation - i can fix this by randomly clicking my stylus buttons, and sometimes the pen starts working.

I tried setting the debug mode to 1 - when it doesnt work i still get BTN_TOUCH events, i just dont get pen down/up events. I also still get BTN_TOOL_PEN proximity events. 

Since the problem seems to be with button clicks, maybe natty narwhal will fix it with that patch?

Edit: oh, and it does have two buttons and does have 1024 sensitivity levels.

---

### Post by Stord on 2011-04-24
Its also really weird - in ubuntu 10.10, wizardpen.conf comes with an options 

MatchTag "wizardpen" 

in the Driver "wizardpen" section. 

This causes the tablet to barely work - if you touch the pen down, and then lift it back up, the mouse will no longer track with the movement of the stylus. If you get rid of this, it will work (if you have the calibration section in)

And if you add

Option  "Rotate90" "1"

the mouse cursor gets stuck at the leftmost side of the screen - you can only move it up and down the left side, plus a little to the right. On the other hand, the tablet is indeed rotated.

---

### Post by Favux on 2011-04-24
OK, let's try the button map.  I'd feel better if the list-props for the WizardPen showed button properties etc. like it should so we aren't so in the dark.  Also notice on the HOW TO there aren't any button Options for the WizardPen driver you can add to the wizardpen.conf.  Try entering in a terminal:
```
xinput set-button-map "WALTOP International Corp. Slim Tablet" 1 3 2
```
and cross your fingers.
> Since the problem seems to be with button clicks, maybe natty narwhal will fix it with that patch? 
It should. Plus you'll have the Waltop on the Wacom X driver where it is suppose to be.  Actually on his Digimend Project site he has kernel patches that should get it working in Lucid or Maverick but I probably wouldn't try that since Natty is almost out.


Edit:  That's why I post a version just for the Waltop.  If I remember right DoctorMO added a udev rule matching the Vendor ID's for WizardPen tablets and that's where the MatchTag match is coming from.  Since a Waltop has a different Vendor ID the tag match blocks out the Waltop.  So I just avoided it rather than add the Waltop to the udev rule since it isn't needed.

---

### Post by Stord on 2011-04-24
Since i dont really need the stylus buttons, i decided to remove it and place a thin layer of tape over the opening so now everything works perfectly :)

Ill probably try later and replace the stylus button with natty narwhal.

---

### Post by Favux on 2011-04-24
That was a clever work a round!

I'm using the Beta 2 now and it seems fairly stable.  But I have to because I have to check out some stuff.  The usual advice is to wait 4-6 weeks after a release so they iron out some of the wrinkles before you install.  But it sounds like you may want/need to install it sooner.  Be warned the first week of a release usually sees the servers being slammed, so if you hold off a week or so the download should go smoother.

---

### Post by Stord on 2011-04-24
Thanks for all the help!

Will do...

---

### Post by Stord on 2011-04-28
Well, i couldnt resist, had to install... Good news, it works! I plug in my gpad, dont have to install any drivers, yahoo!!!

Now i need an xournal which does autosave and isnt too slow moving large graphics around .... waiting for next release:D

---

### Post by Favux on 2011-04-28
Great!

Yeah it'd be nice.  I'm also looking forward to handwriting recognition.

---

