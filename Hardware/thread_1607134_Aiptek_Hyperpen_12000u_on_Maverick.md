---
title: "Aiptek Hyperpen 12000u on Maverick"
date: 2010-10-27
forum: Hardware
---

### Post by naeddyr on 2010-10-27
Hello,

I am trying to get my Aiptek HyperPen 12000u tablet to work on Ubuntu 10.10 x64.

Before installing drivers it works minimally:

- Hovering the stylus works initially. Then, when you use the nib, hovering is lost, and you can move the cursor only by "clicking" and dragging.
- No pressure sensitivity.

I installed the xserver-xorg-input-aiptek package through Synaptic, and then followed what the wiki said for 10.04+10.10 ( [https://help.ubuntu.com/community/AiptekTablet](https://help.ubuntu.com/community/AiptekTablet) ); I created the udev and xorg config files (and I put the 10-aiptek.conf file in /usr/share/X11/xorg.conf.d etc.). I've rechecked these files several times, and they are verbatim to the stuff in the wiki (I even added newlines at the end, I have no idea if that's meaningful but hey).

After doing this, and rebooting (I do not know the black magic that is "restart udev"), it works just as well as it did before-hand.

I searched on the internet for people with the same problem, and someone on a thread on an Arch forum seems to have had the same problem (new Xorg version?). They posted a bit from their Xorg.0.log file where the word "Aiptek" is mentioned, and I'll do the same:
```
[    15.191] (II) config/udev: Adding input device Aiptek (/dev/input/event5)
[    15.191] (**) Aiptek: Applying InputClass "pen"
[    15.191] (**) Aiptek: Applying InputClass "evdev pointer catchall"
[    15.191] (**) Aiptek: Applying InputClass "evdev keyboard catchall"
[    15.191] (**) Aiptek: Applying InputClass "evdev tablet catchall"
[    15.191] (**) Option "SendCoreEvents" "true"
[    15.191] (**) Aiptek: always reports core events
[    15.191] (**) Aiptek: Device: "/dev/input/event5"
[    15.200] (II) Aiptek: Found 3 mouse buttons
[    15.200] (II) Aiptek: Found scroll wheel(s)
[    15.200] (II) Aiptek: Found relative axes
[    15.200] (II) Aiptek: Found x and y relative axes
[    15.200] (II) Aiptek: Found absolute axes
[    15.200] (II) evdev-grail: failed to open grail, no gesture support
[    15.200] (II) Aiptek: Found x and y absolute axes
[    15.200] (II) Aiptek: Found absolute tablet.
[    15.200] (II) Aiptek: Found keys
[    15.200] (II) Aiptek: Configuring as tablet
[    15.200] (II) Aiptek: Configuring as keyboard
[    15.200] (**) Aiptek: YAxisMapping: buttons 4 and 5
[    15.200] (**) Aiptek: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    15.200] (II) XINPUT: Adding extended input device "Aiptek" (type: KEYBOARD)
[    15.200] (**) Option "xkb_rules" "evdev"
[    15.200] (**) Option "xkb_model" "pc105"
[    15.200] (**) Option "xkb_layout" "fi"
[    15.200] (WW) Aiptek: touchpads, tablets and touchscreens ignore relative axes.
[    15.200] (II) Aiptek: initialized for absolute axes.
[    15.200] (II) config/udev: Adding input device Aiptek (/dev/input/mouse1)
[    15.200] (II) No input driver/identifier specified (ignoring)
```

What I think I understand is that evdev is the fail-safe default (which allows the tablet to work at all?), and that the udev stuff fails when it's supposed to load the drivers?

In any case, I would be grateful if someone could help with this.

---

### Post by Favux on 2010-10-27
Hi naeddyr,

> What I think I understand is that evdev is the fail-safe default (which allows the tablet to work at all?), and that the udev stuff fails when it's supposed to load the drivers?
The evdev driver is the fail safe and it tries to pick up a device if nothing else claims it.  But the Aiptek driver should be claiming your tablet, not the evdev driver.  Running the tablet on the evdev driver is why it isn't working too well.  So something isn't right, probably with a match line in the aiptek.conf.

Post the output of:
```
xinput --list
```
in a terminal.  Also post your 50-aiptek.conf (I think it's 50).

---

### Post by naeddyr on 2010-10-27
input --list:

```
&#9121; Virtual core pointer                            	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                    	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB-PS/2 Optical Mouse                	id=8	[slave  pointer  (2)]
&#9116;   &#8627; Microsoft Natural® Ergonomic Keyboard 4000	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Aiptek                                      	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                         	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                	id=5	[slave  keyboard (3)]
    &#8627; Power Button                               	id=6	[slave  keyboard (3)]
    &#8627; Power Button                               	id=7	[slave  keyboard (3)]
    &#8627; Microsoft Natural® Ergonomic Keyboard 4000	id=9	[slave  keyboard (3)]

```

And as I said, I copied what was written on the wik.. er, now that I look at it, [the help section]("https://help.ubuntu.com/community/AiptekTablet"), where it was said to create **/usr/share/X11/xorg.conf.d/10-aiptek.conf**, and the contents is:

```
Section "InputClass"
        Identifier "pen"
        MatchProduct "Aiptek|AIPTEK|aiptek"
        MatchDevicePath "/dev/input/event*"
        Driver "aiptek"
        Option "SendCoreEvents" "true"
        Option "USB" "on"
        Option "Type" "stylus"
        Option "Mode" "absolute"
        Option "zMin" "0"
        Option "zMax" "511"
EndSection

```

verbatim from the article.

---

### Post by Favux on 2010-10-27
Everything looks right.  Before we start messing with the .conf let's try to ensure the driver installed correctly.  In Synaptic Package Manager verify that the xserver-xorg-input-aiptek driver package is installed.  If it isn't install it; if it is reinstall it and reboot.  You may need to reboot a few times for things to shake out.

---

### Post by naeddyr on 2010-10-27
Yes, it was installed.

I reinstalled it, and rebooted twice. It's still stuck using the evdev drivers.

You thought the .conf file should be named 50-aiptek.conf. Is the number significant? In usr/share/X11/xorg.conf.d/ there are several .conf files, most of which are 50, some 51 and a 60, while the evdev catchall rules are in 10-evdev.conf (and the aiptek rules I copied are in 10-aiptek.conf). Does Xorg start with big numbers and go down the list?

---

### Post by Favux on 2010-10-27
No the other way around.  Lower numbers first and then up to larger numbers.  I did have a WizardPen user tell me when he changed the .conf from 70 to 50 it stopped working.  I don't know why.  So something to think about.  Say going from 10 to 50 like the Wacom .conf did.

We'll use baby steps.  Try:
```
Section "InputClass"
        Identifier "Aiptek class"
        MatchProduct "Aiptek|AIPTEK|aiptek"
        MatchDevicePath "/dev/input/event*"
        Driver "aiptek"
#        Option "SendCoreEvents" "true"
        Option "USB" "on"
        Option "Type" "stylus"
        Option "Mode" "absolute"
        Option "zMin" "0"
        Option "zMax" "511"
EndSection
```
The wiki is wrong.  "SendCoreEvents" is no longer needed for X servers 1.7 (Lucid) and up.  Don't think it hurts, but...  Also "pen" is not informative.  You'll know it's working when in Xorg.0.log you see something like:
```
[    15.191] (**) Aiptek: Applying InputClass "evdev pointer catchall"
[    15.191] (**) Aiptek: Applying InputClass "evdev keyboard catchall"
[    15.191] (**) Aiptek: Applying InputClass "evdev tablet catchall"
[    15.191] (**) Aiptek: Applying InputClass "Aiptek class"

```
instead of:
```
[    15.191] (**) Aiptek: Applying InputClass "pen"
[    15.191] (**) Aiptek: Applying InputClass "evdev pointer catchall"
[    15.191] (**) Aiptek: Applying InputClass "evdev keyboard catchall"
[    15.191] (**) Aiptek: Applying InputClass "evdev tablet catchall"

```
Last driver mentioned is the one that should have the tablet.  So you can see why I'm wondering about the .conf number.

---

### Post by naeddyr on 2010-10-27
[SIZE="1"]One two! One two! And through and through,
the sudo vim went snicker-snack!
Callooh calay! What a joyous day!
[/SIZE]

I renamed the file to 50-aiptek.conf, and made the changes (including the comment), rebooted and now:

+ hovering works
+ the side buttons work
- the pressure sensitivity doesn't work, but this is at the very least usable. I only tested this in GIMP, so it might just be that. (TEST). doesn't work in Inkscape either.

I'll copy from Xorg.0.log here:

```
[    14.831] (II) config/udev: Adding input device Aiptek (/dev/input/event5)
[    14.831] (**) Aiptek: Applying InputClass "evdev pointer catchall"
[    14.831] (**) Aiptek: Applying InputClass "evdev keyboard catchall"
[    14.831] (**) Aiptek: Applying InputClass "evdev tablet catchall"
[    14.831] (**) Aiptek: Applying InputClass "Aiptek class"
[    14.831] (II) LoadModule: "aiptek"
[    14.831] (II) Loading /usr/lib/xorg/modules/input/aiptek_drv.so
[    14.846] (II) Module aiptek: vendor="X.Org Foundation"
[    14.846] 	compiled for 1.8.99.905, module version = 1.3.0
[    14.846] 	Module class: X.Org XInput Driver
[    14.846] 	ABI class: X.Org XInput driver, version 11.0
[    14.846] (II) xf86AiptekInit(): begins
[    14.846] (**) xf86AiptekConfig: device not shared btw Aiptek and Power Button
[    14.846] (**) xf86AiptekConfig: device not shared btw Aiptek and Power Button
[    14.846] (**) xf86AiptekConfig: device not shared btw Aiptek and Logitech USB-PS/2 Optical Mouse
[    14.846] (**) xf86AiptekConfig: device not shared btw Aiptek and Microsoft Natural® Ergonomic Keyboard 4000
[    14.846] (**) xf86AiptekConfig: device not shared btw Aiptek and Microsoft Natural® Ergonomic Keyboard 4000
[    14.846] (**) xf86AiptekConfig: device not shared btw Aiptek and Aiptek
[    14.846] (**) Aiptek: always reports core events
[    14.846] (**) Option "Device" "/dev/input/event5"
[    14.851] (==) HID Device name: "Aiptek"
[    14.851] (==) HID Driver Version: 1.0.1
[    14.851] (==) HID Driver knows it has 1 devices configured
[    14.851] (==) HID Driver is using 28 as the fd
[    14.851] From ioctl() xCapacity=5999
[    14.851] From ioctl() yCapacity=4499
[    14.900] (**) Aiptek device is /dev/input/event5
[    14.900] (**) Aiptek is in absolute mode
[    14.900] (**) Option "USB" "on"
[    14.900] (**) Aiptek: reading USB link
[    14.900] (**) Option "ZMax" "511"
[    14.900] (**) Aiptek: ZMax/MaxZ = 511
[    14.900] (**) Option "ZMin" "0"
[    14.900] (**) Aiptek: ZMin/MinZ = 0
[    14.900] (**) Option "BaudRate" "9600"
[    14.900] (**) Aiptek: BaudRate 9600
[    14.900] (**) Aiptek: xf86AiptekInit() finished
[    14.900] (II) XINPUT: Adding extended input device "Aiptek" (type: Stylus)
[    14.940] (==) HID Device name: "Aiptek"
[    14.940] (==) HID Driver Version: 1.0.1
[    14.940] (==) HID Driver knows it has 1 devices configured
[    14.940] (==) HID Driver is using 28 as the fd
[    14.940] From ioctl() xCapacity=5999
[    14.940] From ioctl() yCapacity=4499
[    14.940] (**) xTop invalid; adjusted to 0
[    14.940] (**) yTop invalid; adjusted to 0
[    14.940] (**) xBottom invalid; adjusted to 5999
[    14.940] (**) yBottom invalid; adjusted to 4499
[    14.940] (**) ScreenNo invalid; adjusted to 0
[    14.940] Able to open aiptek device
[    14.940] (II) config/udev: Adding input device Aiptek (/dev/input/mouse1)
[    14.940] (II) No input driver/identifier specified (ignoring)]
```

I could try reproducing the non-working setup by renaming the file back to 10-aiptek.conf or changing back to the pen class.

Could the last lines in the log be referring to the mouse that comes works with the tablet? I only use the stylus, so I have no idea where that thing is.

---

### Post by Favux on 2010-10-27
Hi naeddyr,

Outstanding!  :)

My guess is the change from 10 to 50 is what did it.  I wonder if going to 20 would have been enough?

For Pressure in Gimp and Inkscape did you configure the extended input devices?  See near the bottom of the Wacom wiki:  [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)  Also does your tablet have 512 or 1024 levels of pressure?

If you have an Aiptek tablet mouse we can try to get it working if you want.  We'd have to add another snippet to the 50-aiptek.conf.  If you find it.

---

### Post by naeddyr on 2010-10-27
Yessshh!

Ok, here's a small summary:

It's the number. 10-aiptek.conf doesn't work. 20-aiptek.conf and 50-aiptek.conf do. This should be changed in the wiki. :)

Changing the "Aiptek class" bit back to "pen" doesn't cause it to fail (is it only a descriptor for humans in the logs?) Didn't try uncommenting the core events line.

And yes, I'd forgotten to configure extended input in GIMP and inkscape. Now the pressure works perfectly!

I'll [Solve] this and get to my super important tabletting stuff now. :)

Thanks, Favux! :KS

EDIT:

the Aiptek HyperPen 12000u has max. 512 levels of pressure.

EDIT:

Civilians can't [Solved]. :(

---

### Post by Favux on 2010-10-27
> is it only a descriptor for humans in the logs?
Yes.
> Civilians can't [Solved].
I thought they restored that function.   It should be in Thread Tools on top right of first post on the thread.

---

