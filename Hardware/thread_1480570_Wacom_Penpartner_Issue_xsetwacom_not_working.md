---
title: "Wacom Penpartner Issue: xsetwacom not working"
date: 2010-05-11
forum: Hardware
---

### Post by mikeashelby on 2010-05-11
Hi Guys,

I've trawled the forums for any advice, and come up short. The issue I have is this:

My penpartner is working - to a degree. It only registers the stylus location when touching (and therefore clicking on) the tablet. As such, you can't really use it! Infuriating, as it worked perfectly out of the box on my 9.10 install!

Anyway, I was going to try some of the xsetwacom parameters, and see if that helped. Unfortunately, I can't get it to give me my device name: xsetwacom --list dev doesn't return anything!

Any help would be amazing.

Thanks in advance,

Mike (running 10.04)

---

### Post by mikeashelby on 2010-05-11
I've managed to find the dev_name using "xinput --list", which is a good start I think!

However, none of the parameters seem to work. 

```
xsetwacom set "Wacom Penpartner" Mode Relative
```

gives

```
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  144 (XInputExtension)
  Minor opcode of failed request:  5 (X_SetDeviceMode)
  Serial number of failed request:  15
  Current serial number in output stream:  15
```

So... not sure this is going to help me much...

A little progress... though not a lot!

---

### Post by wankel on 2010-05-11
Does the tablet need xorg.conf? That is not available by default if kernel mode settings are used (KMS). 

If you did not do that yet, check what is available in /etc/X/ .

Good luck!

---

### Post by mikeashelby on 2010-05-11
... and the bad news is... It's now (after another reboot) stopped working at all!

However - a lot more of the properties are now available (and returning values with xsetwacom get "Wacom Penpartner" all).

Still unable to set values though (gives similar to above response)... Hmmm.

Argh!

---

### Post by mikeashelby on 2010-05-11
How do I "check what is available in /etc/X/"?

---

### Post by Favux on 2010-05-11
Hi mikeashelby,

Is your Wacom Penpartner a serial tablet or usb tablet?

---

### Post by mikeashelby on 2010-05-12
It's a usb. It's the original A6 usb penpartner. Over 10 years old now!

---

### Post by Favux on 2010-05-12
Hi mikeashelby,

Since it's ten years old I checked the source code to see if it's in there and it is.  In fact it's the first entry!  The wacom.ko (the usb kernel driver; I think the linuxwacom version 0.8.4-4 is in Lucid) wacom_wac.c has it:
```
static struct wacom_features wacom_features[] = {
	{ "Wacom Penpartner",        7,   5040,  3780,  255,  0, PENPARTNER },
```
And the xf86-input-wacom (the X driver for Lucid's Xserver 1.7) has it.  In the wcmUSB.c:
```
	static WacomModel usbPenPartner =
	{
		"USB PenPartner",
		usbInitProtocol4,
		NULL,                 /* resolution not queried */
		usbWcmGetRanges,
		NULL,                 /* start not supported */
		usbParse,
		wcmFilterCoord,   /* input filtering */
		usbDetectConfig,      /* detect hardware buttons etc */
	};
```
So that's not the problem.  Let's look at your output from:
```
xinput --list
```
in a terminal.

---

### Post by mikeashelby on 2010-05-13
Thanks so much for your help. Yeah - it's a weird one. On 8.4 it worked after some tweaking, in 9.10 it worked out of the box as it were, and now in 10.04 it's gone again!

```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Penpartner                        	id=8	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB-PS/2 Optical Mouse         	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]

```

---

### Post by Favux on 2010-05-13
OK, so the name is right.  You could also try the ID number, 8.

Have you tried the TPCButton command yet?:
```
xsetwacom set "Wacom Penpartner" TPCButton "off"
```

---

### Post by mikeashelby on 2010-05-14
That at least doesn't give an error... but doesn't make it work! What's it meant to do?

It's weird, 'cos for a little while (one login) it worked, but only if I was clicking would it register the location. Then, after a reboot, it stopped working at all... I wonder what I did to break it!

Thanks again for your help... it's a mystery to me!

---

### Post by Favux on 2010-05-14
Hi mikeashelby,

TPC stands for tablet pc and on it means tip touching is left click.  Off is more like hover mode.  So mode relative doesn't appear to be an allowed command for your tablet.

Alright, lets hope something went wrong with the install of the Wacom driver and all we need to do is reinstall it.  In Synaptic Package Manager search for xserver-xorg-input-wacom.  Right click on it and tell it to reinstall and then reboot.

If that doesn't work we'll check out the wacom.ko, the usb kernel driver.

---

### Post by mikeashelby on 2010-05-15
Hey,

Cheers for this. Tried the reinstall and restart now, and, alas, it's still not having any joy.

Heading to the Kernel sounds like a scary task - but we've come this far!

Thanks again for your help,

Mike

---

### Post by mikeashelby on 2010-05-18
Anyone?!

---

### Post by Favux on 2010-05-18
Hi mikeashelby,

What we want to do is verify that the wacom.ko, the usb kernel driver/module, is auto-loading.  It doesn't on some systems.  So to see if it is loading enter in a terminal:
```
lsmod | grep [Ww]acom
```
Should see 'wacom' in the output.

---

### Post by mikeashelby on 2010-05-18
Yep. wacom (in red) then 26872 0...

Is that doing what you were expecting?

---

### Post by Favux on 2010-05-18
Yes, so it is loading.  That means you have both the X driver and usb driver loaded and working so that isn't the problem.

I assume you haven't entered any wacom entries in your xorg.conf, correct?  So maybe we need to play with the the 10-wacom.conf in /usr/lib/X11/xorg.conf.d/.  How many buttons does your stylus have and does it have an eraser?

---

### Post by mikeashelby on 2010-05-18
Hey,

I don't think I've entered anything in there. It's got a nib, one button, and it does have an eraser, but it stopped working properly a few years back... only registers when pressing down a bit.

Cheers again for your help!

Mike

---

### Post by Favux on 2010-05-18
Alright, let's start playing with the options in the 10-wacom.conf at /usr/lib/X11/xorg.conf.d/.  Edit with:
```
gksudo gedit /usr/lib/X11/xorg.conf.d/10-wacom.conf
```
Change the usb snippet/section, which should look close to this:
```
Section "InputClass"
	Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#	MatchProduct "Wacom|WALTOP|WACOM"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection
```
to:
```
Section "InputClass"
	Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#	MatchProduct "Wacom|WALTOP|WACOM"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
	Option "Button1" "1"
	Option "Button2" "3"
	Option "Button3" "3"
EndSection
```
Save, Close, and reboot.  And see if that gets us anywhere.  By the way 'Option "Button2" "3"' should make the stylus button a right mouse click.

---

### Post by mikeashelby on 2010-05-18
Right. No cigar this time, but it did look exactly as you thought it would!

What's next senai?

---

### Post by Favux on 2010-05-18
Hmm.  Did at least the stylus button become a right mouse click?

At this point I'm wondering about a mechanical problem with the stylus.  This is made more likely since you say you already have one with the eraser.  I have seen at least one other case where the stylus tip was broken.  To rule this out does the stylus work OK in Windows?

The other option seems to be a bug in the linuxwacom code for the PenPartner.

---

### Post by mikeashelby on 2010-05-19
Alas, to your first question, no. It's not registering anything...

It's working in windows (I made a special trip into MS land just to check!), and the little light which registers clicks is still flashing in ubuntu when I press down or right click...

It's really weird, because one time, and one time only (since being in 10.04) it registered where the pen was whenever I clicked... and before (since 'upgrading' from 9.10 ;) and since then - nothing at all.

I'm wondering if I messed something up in trying to get it to work the first time - but I've pretty much lost track now...

Any further thoughts?

---

### Post by Favux on 2010-05-19
Well, next I was going to suggest we play with some other options like:
```
Option "Threshold" "number"
Option "CursorProx" "number"
Option "Suppress" "number"

```
Those are from:  [http://linuxwacom.sourceforge.net/index.php/howto/inputdev](http://linuxwacom.sourceforge.net/index.php/howto/inputdev)

Or the xsetwacom commands:
```
ClickForce     integer (1 - 21)         sets tip/eraser pressure threshold with clickforce scale
CursorProx     integer (distance)       sets cursor distance margin for proximity-out 
				           in distance from the tablet surface

```
Although cursor probably refers to the Wacom tablet mouse.  From:  [http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom](http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom)

But if the button option isn't working I don't know if these would do any good.

---

### Post by mikeashelby on 2010-05-21
Yeah - alas. As you predicted, this doesn't help. Can't fathom it. Don't know what I've done to mess it up, but it's a gonner as far as it seems at the moment...

Thanks for all your help... Might go back to retry some of the stuff I tried before in terms of installing - see how that goes.

Again - many thanks for your help. It really is appreciated.

---

### Post by mikeashelby on 2010-05-28
Hmmm... 6 days on, and still no joy, save for noticing that someone else is having the same problem (and it seems to be that only the eraser is appearing in the xsetwacom --list --verbose list...).

Any further clues from anyone?!

---

### Post by Favux on 2010-05-28
Not seeing stylus in 'xsetwacom list' is a big clue.  Let's look at your Xorg.0.log, located in /var/log.  You can compress it by right click Create Archive and attach it to your next post with Manage Attachments below.  That will tell us if the wacom driver is declaring errors at boot.

---

### Post by mikeashelby on 2010-05-28
Right... let's see if this helps. There are a few lines that I'd think are potentially of interest:

```
(II) Wacom Penpartner: type not specified, assuming 'eraser'.
```

for example.

Let me know if this yeilds any clues!

---

### Post by Favux on 2010-05-28
Hi mikeashelby,

OK, the Xorg.0.log doesn't make a lot of sense:
```
(II) config/udev: Adding input device Wacom Penpartner (/dev/input/event4)
(**) Wacom Penpartner: Applying InputClass "evdev touchscreen catchall"
(**) Wacom Penpartner: Applying InputClass "Wacom class"
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.10.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Option "Device" "/dev/input/event4"
(II) Wacom Penpartner: type not specified, assuming 'eraser'.
(II) Wacom Penpartner: other types will be automatically added.
(**) Wacom Penpartner: always reports core events
(II) Wacom Penpartner: hotplugging dependent devices.
(II) Wacom Penpartner: hotplugging completed.
(II) XINPUT: Adding extended input device "Wacom Penpartner" (type: ERASER)
(--) Wacom Penpartner: using pressure threshold of 15 for button 1
(--) Wacom Penpartner: Wacom USB PenPartner tablet speed=38400 maxX=5040 maxY=3780 maxZ=255 resX=1000 resY=1000  tilt=disabled
(--) Wacom Penpartner: top X=0 top Y=0 bottom X=5040 bottom Y=3780 resol X=1000 resol Y=1000
(II) config/udev: Adding input device Wacom Penpartner (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
```
It's acting like there is no stylus at all, just the eraser.  The eraser should be a sub-device of stylus.  Yet we know the stylus works because you checked it out in Windows.

Let's try using xorg.conf.  Do you have one at /etc/X11?

---

### Post by mikeashelby on 2010-05-29
Right. I've just looked at my xorg.conf and that says:

```
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
	Option	"AddARGBGLXVisuals"	"True"
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

I have added wacom things to another file (10-wacom.conf I think) before, but should there be something in this file?

I'm off on holiday for a few days from later today, so apologies if I don't get back to you before Thursday...

Cheers,

m

---

### Post by Favux on 2010-05-29
No, no wacom sections should be present in xorg.conf.  But since stylus isn't showing up with the 10-wacom.conf configuring things we are going to try configuring through xorg.conf instead.

So I'll write some wacom sections for xorg.conf for you.  To do that I need to know what wacom devices you have.  Stylus, how many buttons on the stylus?  Eraser?  Wacom tablet mouse?  Anything else?

Enjoy your holiday!

---

### Post by mikeashelby on 2010-06-03
Right. Well, my pen is one of the most basic setups. It's only the pen (no mouse) and the pen has a pressure sensitive tip, button on the side, and a pressure sensitive eraser (at least, it should!).

Other than that, it's just the A6 pad itself.

Cheers. Had a great few days away!

---

### Post by Favux on 2010-06-03
Hi mikeashelby,

Alright, assuming ttyS0 is the right serial port, as it usually is, try the following test1 xorg.conf.  As always when messing with one of these Xorg configuration files, in this case xorg.conf, back up your current working version and be prepared to restore it from the command line in case we break X.

---

### Post by mikeashelby on 2010-06-04
Hey,

I tried that - and alas no joy. It is a USB one, so I tried commenting out the serial bits, and uncommenting the USB bits, but still no joy...

---

### Post by Favux on 2010-06-07
Hi mike,

Oops, color me embarassed.  I even know how I managed that.  I labeled your xorg.conf serial when I was organizing and labeling stuff.

Anyway this is what it should look like using the wacom symlink.  This will work if you have 69-xserver-xorg-input-wacom.rules in place in Lucid at "/lib/udev/rules.d/".  And it should be, it is installed by the xserver-xorg-input-wacom package.

By the way the PenPartner symlink rule is the first one in the table:
```
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0000", SYMLINK+="input/tablet-penpartner"
```

---

### Post by mikeashelby on 2010-06-08
Given it a go... no joy. That rule thing does exist, and the first line of that list looks exactly like the one above - so guessing that's not the problem.

You do seem to be a fountain of knowledge on this - and your time spent is much appreciated!

---

### Post by Favux on 2010-06-08
Hmmm.  Since you have the 69-etc.-wacom.rules in place, using the test2 xorg.conf with it's symlinks let's look at your Xorg.0.log in /var/log again and see what it is telling us this time.  Right click and use Create Archive to compress and attach it to your next post with Manage Attachments.

---

### Post by mikeashelby on 2010-06-09
Right. Here's the log... hope this means something to you!?

Cheers.

---

### Post by Favux on 2010-06-09
Hi mikeashelby,

This shouldn't be this hard or be taking this long.  Thanks for hanging in there.  :)

OK, since we're using xorg.conf be sure to have the tablet plugged in before boot, which I think you are doing.

Despite the xorg.conf symlinks now apparently working, the Xorg.0.log is similar to the last.  Wacom seems to be loading alright:
```
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.10.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
```
Then it starts loading the tablet:
```
(**) Option "Device" "/dev/input/wacom"
(II) UnloadModule: "wacom"
(EE) PreInit returned NULL for "stylus"
(**) Option "Device" "/dev/input/wacom"
(**) eraser: always reports core events
(II) XINPUT: Adding extended input device "eraser" (type: ERASER)
(--) eraser: using pressure threshold of 15 for button 1
(--) eraser: Wacom USB PenPartner tablet speed=38400 maxX=5040 maxY=3780 maxZ=255 resX=1000 resY=1000  tilt=disabled
(--) eraser: top X=0 top Y=0 bottom X=5040 bottom Y=3780 resol X=1000 resol Y=1000
```
and we again see the same error:
```
(EE) PreInit returned NULL for "stylus"
```
So stylus fails on preinit, although eraser sets up!  **This is looking more and more like a bug in the xf86-input-wacom code.**  Then the evdev driver picks up any unclaimed input device like it is suppose to:
```
(II) config/udev: Adding input device Wacom Penpartner (/dev/input/event4)
(**) Wacom Penpartner: Applying InputClass "evdev touchscreen catchall"
(**) Wacom Penpartner: Applying InputClass "Wacom class"
(**) Option "Device" "/dev/input/event4"
(II) Wacom Penpartner: type not specified, assuming 'eraser'.
(II) Wacom Penpartner: other types will be automatically added.
(WW) Wacom Penpartner: device file already in use by eraser. Ignoring.
(II) UnloadModule: "wacom"
(EE) PreInit returned NULL for "Wacom Penpartner"
(II) config/udev: Adding input device Wacom Penpartner (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
```
Notice how it notices eraser is already claimed by the device file.  So bottom line it doesn't look like using the xorg.conf over the 10-wacom.conf gained us anything.

Hmmm.  Let's look at a few last things.  I guess leave the xorg.conf in and the same as for the last Xorg.0.log.  What we should look at is the entire output of the following.

Let's make sure that usb communication through the wacom.ko seems good:
```
dmesg | grep [Ww]acom
```
Let's see what the  usb by-paths look like:
```
ls -l /dev/input/by-path
```
Then let's see what xinput (the Xserver) is seeing:
```
xinput --list
```
And finally what the Wacom X driver (well xsetwacom, but it amounts to the same thing) sees:
```
xsetwacom list
```
I'm thinking, unless we get lucky, you're going to have to post to linuxwacom-discuss and ask for help.  Hopefully I'm missing something obvious but it may be a bug in the code.  The ouputs above and in the other posts should give you good info. to post which will be helpful.

---

### Post by mikeashelby on 2010-06-09
Well, the first one gave this:

```
[   14.909064] input: Wacom Penpartner as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/input/input4
[   14.928140] usbcore: registered new interface driver wacom
[   14.928143] wacom: v1.52:USB Wacom tablet driver

```

The Second one gave:

```
total 0
lrwxrwxrwx 1 root root 9 2010-06-09 15:17 pci-0000:00:1d.0-usb-0:1:1.0-wacom -> ../event4
lrwxrwxrwx 1 root root 9 2010-06-09 15:17 pci-0000:00:1d.2-usb-0:1:1.0-event-mouse -> ../event5
lrwxrwxrwx 1 root root 9 2010-06-09 15:17 pci-0000:00:1d.2-usb-0:1:1.0-mouse -> ../mouse2
lrwxrwxrwx 1 root root 9 2010-06-09 15:17 platform-i8042-serio-0-event-kbd -> ../event3
```

Then we have:

```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; eraser                                  	id=6	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB-PS/2 Optical Mouse         	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
```

and finally:

```
eraser           ERASER    

```

You're right that it's taking longer than I expected; but think it's me who should be thanking you for sticking in there! I after all, will get (hopefully) a working tablet out of this!

I hope something above helps!

Cheers!

m

---

### Post by Favux on 2010-06-09
Hi mike,

OK, the dmesg seems to show good usb communication with the tablet on input4.  And sure enough it is matched by pci usb event4 input node.  So there should be input available for the driver to grab, like the eraser seems to be doing.  By the way your usb by-path which you could use in xorg.conf instead of the symlink appears to be:
```
	Option "Device" "/dev/input/by-path/pci-0000:00:1d.0-usb-0:1:1.0-wacom"
```

What's interesting is your first xinput showed:
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Penpartner                        	id=8	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB-PS/2 Optical Mouse         	id=9	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
```
Where 'Wacom Penpartner  id=8' was presumably your stylus.  But no eraser and then it disappeared and eraser appeared.  You should see both, in both xinput and xsetwacom.

You could comment out the Wacom sections in xorg.conf, including the "ServerLayout" lines and go back to the 10-wacom.conf in default state and reboot.  And then retry the commands above and see if it makes a difference.  I kind of doubt it.

I think we may be looking at a bug in the code.  But anyway you need to post in linuxwacom-discuss for help from someone who knows more than me:  [https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss](https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss)

You've got plenty of details for them.  They'll also want to know your kernel:
```
cat /proc/version_signature
```
and Xserver version:
```
X -version
```

Good luck!

---

### Post by jonhurst on 2010-12-11
Hi Guys, 

Did you ever have any joy with this. I have exactly the same issue.

---

### Post by mikeashelby on 2011-01-12
Right. I thought I'd give this another try after loads of os updates and such, I thought I'd plug it back in...

No joy initially, but then followed these instructions:

[http://www.xs4all.nl/~oce/beos/wacomxubuntu.html]("http://www.xs4all.nl/~oce/beos/wacomxubuntu.html")

and now it works! I'm sure we'd been through all that sort of stuff... but suffice to say, I'm now clicking away quite happily (haven't yet got the side button or eraser working, but it's a significant start!).

Hope this helps someone!

---

### Post by mikeashelby on 2011-01-12
Just tried to get my side button doing a right click, and not having any joy.

This is in my xorg.conf

```
Section "InputDevice"
	Driver "wacom"
	Identifier "stylus"
	Option "Device" "/dev/input/tablet-penpartner"
	Option "Type" "stylus"
	Option "Mode" "Absolute"
	Option "USB" "on"
	Option "Button1" "1"
	Option "Button2" "2"
	Option "Button3" "3"
EndSection
```

and this in my 50-wacom.conf

```
Section "InputClass"
	Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#	MatchProduct "Wacom|WALTOP|WACOM"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
        #Option "Button2" "2"
        #Option "Button3" "3"
        
EndSection
```

I've done some fiddling with the button numbers (and obviously removed the remark '#' before the relevant lines...) but to no avail...

It's still good to have the pen back, but does anyone have any ideas on this one?

Oh, and thanks again to Fauvx for sticking with me so long on trying to get this working before!

m

---

### Post by Owl_Express on 2011-04-26
Hello,
I just found again my old PenPartner tablet And I tried to re-activate it, My computer is set with Maverick Meerkat and I just found your thread

```

**dmesg | grep [Ww]acom**
[    8.270163] input: Wacom Penpartner as /devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5.4/1-5.4:1.0/input/input5
[    8.294495] usbcore: registered new interface driver wacom
[    8.294502] wacom: v1.52-input-wacom-0.1:USB Wacom tablet driver

``````

**ls -l /dev/input/by-path**
total 0
lrwxrwxrwx 1 root root 9 2011-04-26 23:07 pci-0000:00:1d.1-usb-0:1:1.0-event-kbd -> ../event2
lrwxrwxrwx 1 root root 9 2011-04-26 23:07 pci-0000:00:1d.1-usb-0:1:1.1-event -> ../event3
lrwxrwxrwx 1 root root 9 2011-04-26 23:07 pci-0000:00:1d.2-usb-0:2:1.0-event-mouse -> ../event4
lrwxrwxrwx 1 root root 9 2011-04-26 23:07 pci-0000:00:1d.2-usb-0:2:1.0-mouse -> ../mouse0
lrwxrwxrwx 1 root root 9 2011-04-26 23:07 pci-0000:00:1d.7-usb-0:5.1:1.0-event -> ../event6
lrwxrwxrwx 1 root root 9 2011-04-26 23:07 pci-0000:00:1d.7-usb-0:5.4:1.0-wacom -> ../event5

``````

**xinput --list**
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; HID Keyboard Device                         id=9    [slave  pointer  (2)]
&#9116;   &#8627; Logitech Optical USB Mouse                  id=10    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Penpartner eraser                     id=12    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; HID Keyboard Device                         id=8    [slave  keyboard (3)]
    &#8627; UVC Camera (046d:0802)                      id=11    [slave  keyboard (3)]

``````

**xsetwacom list**
Wacom Penpartner eraser             id: 12    type: ERASER    

``````

**cat /proc/version_signature**
Ubuntu 2.6.35-29.51-generic 2.6.35.12

``````

**X -version**

X.Org X Server 1.9.0
Release Date: 2010-08-20
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
Current Operating System: Linux dell-sx280-brusset 2.6.35-29-generic #51-Ubuntu SMP Fri Apr 15 17:13:54 UTC 2011 i686
Kernel command line: root=UUID=45b34ebf-3c2c-46b4-8ed8-325e42fbafcc ro quiet splash 
Build Date: 09 January 2011  12:14:58PM
xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.18.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.

```
I Think my issue is the same as mikeashelby : The eraser works but not the pen nor the button.

Before going here I tried some tricks I found elsewhere ... and I activated Dr MO's PPA : ppa:doctormo/wacom-plus
I installed wacom-dkms and xserver-xorg-input-wacom but with no more positive results.
Does anyone can help me ?

---

