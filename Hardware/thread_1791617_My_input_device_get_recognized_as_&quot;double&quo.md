---
title: "My input device get recognized as &quot;double&quot; (two times)"
date: 2011-06-27
forum: Hardware
---

### Post by alexan on 2011-06-27
When I plug my usb pen tablet the dmesg show:
```
[ 4312.478781] usb 3-1: new low speed USB device using uhci_hcd and address 5
[ 4312.761005] input: UC-LOGIC Tablet WP5540U as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input14
[ 4312.761263] input: UC-LOGIC Tablet WP5540U as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input15
[ 4312.761442] uclogic 0003:5543:0004.0004: input,hidraw0: USB HID v1.00 Mouse [UC-LOGIC Tablet WP5540U] on usb-0000:00:1d.1-1/input0
```


And thus **xinput list** show:

```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
[...]
&#9116;   &#8627; UC-LOGIC Tablet WP5540U                 	id=13	[slave  pointer  (2)]
&#9116;   &#8627; UC-LOGIC Tablet WP5540U                 	id=14	[slave  pointer  (2)]
[...]

```

But lsusb is fine:
```
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 5543:0004 UC-Logic Technology Corp. Genius MousePen 5x4 Tablet
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
The result of this, is that I've random problem with Gimp, can't use with Inkscape and (strangely) MyPaint work flawlessly.

Any way to remove the extra (shadow copy) input device?

---

### Post by Favux on 2011-06-27
Hi alexan,

That is most likely due to a spurious mouse entry for your tablet.

Your 70-wizardpen.conf in /usr/share/X11/xorg.conf.d should have two snippets.  The second snippet should be a mouse ignore one with the option:
```
Option "Ignore"  "yes"
```
after the wizardpen driver line.  Please post the contents.

---

### Post by alexan on 2011-06-28
In Natty there's no *70-wizardpen.conf*
Instead there's some "catchall" call in cat *10-evdev.conf*

```
#
# Catch-all evdev loader for udev-based systems
# We don't simply match on any device since that also adds accelerometers
# and other devices that we don't really want to use. The list below
# matches everything but joysticks.

Section "InputClass"
        Identifier "evdev pointer catchall"
        MatchIsPointer "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev keyboard catchall"
        MatchIsKeyboard "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev touchpad catchall"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev tablet catchall"
        MatchIsTablet "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev touchscreen catchall"
        MatchIsTouchscreen "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection
```
By setting ignore to "**Identifier "evdev tablet catchall**"
and generating a new 70-wizardpen.conf with contentes:
```
Section "InputDevice"
        Identifier      "WizardPen Tablet"
        Option          "SendCoreEvents"        "true"
        Driver          "wizardpen"
        Option          "Device"        "/dev/tablet-event"
        Option          "TopX"          "2199"
        Option          "TopY"          "3598"
        Option          "BottomX"       "30325"
        Option          "BottomY"       "29278"
EndSection
```
In this way I'd managed to have a single in the xinput -list **not** working.
[s]Now I am going to install wizardpen driver from ppa to see if this resolve anything.[/s]
No, installing wizardpen from ppa don't solve anything.

Summary:
when the "catchall" in *10-evdev.conf* is enabled I have two windardpen enabled: working so so with some software
when disabled the "catchal" and pug in the specific 70-wizardpen.conf I've only one wizardpen in xinput list... in which don't work at all



NB: the same problem apply through live.

---

### Post by Favux on 2011-06-28
Hi alexan,

You do not need to modify the evdev.conf at all and shouldn't.  Assuming the PPA wizardpen driver from DoctorMO is installed.  And the PPA package should automatically install a 70-wizardpen.conf for you in /usr/share/X11/xorg.conf.d.  You're release is Natty correct?  The PPA has been updated for Natty correct?

The wizarpen.conf you show isn't correct because it does not have a separate snippet to block the spurious mouse entry with the "Ignore" option.

The question is what driver is the tablet on.  You can check by using the "device name" from the *xinput list* output.  The check the driver the device is on in the output of:
```
xinput list-props "device name"
```
Or you can check your Xorg.0.log in /var/log.

In a few cases the PPA wizardpen.conf doesn't work because the tablet is new or it is a "corner" case.  In other words the re-brander did something different with the underlying UC-LOGIC WP5540U tablet.

So reinstall the PPA driver if need be and check that the 70-wizardpen.conf is installed.  Check that your tablet stylus is on the driver and mouse isn't on a driver.  If not post the 70-wizardpen.conf and the output of *xinput list*.

---

### Post by alexan on 2011-06-28
Ok, here we go.
My wizardpen tablet is a re-branded from Trust in [stylus design tablet](http://www.trust.com/products/product.aspx?artnr=15356)
The same problem apply to natty launch from live... basically the tablet works, but it get recognized two time.

the command:
**xinput list-props "UC-LOGIC Tablet WP5540U"**:
```
Warning: There are multiple devices matching 'UC-LOGIC Tablet WP5540U'.
To ensure the correct one is selected, please use the device ID, or prefix the
device name with 'pointer:' or 'keyboard:' as appropriate.

unable to find device UC-LOGIC Tablet WP5540U
```

So I do:
**xinput list-props 13**
```
Device 'UC-LOGIC Tablet WP5540U':
	Device Enabled (139):	1
	Coordinate Transformation Matrix (141):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (258):	0
	Device Accel Constant Deceleration (259):	1.000000
	Device Accel Adaptive Deceleration (260):	1.000000
	Device Accel Velocity Scaling (261):	10.000000
```

and
**xinput list-props 14**
```
Device 'UC-LOGIC Tablet WP5540U':
	Device Enabled (139):	1
	Coordinate Transformation Matrix (141):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (258):	0
	Device Accel Constant Deceleration (259):	1.000000
	Device Accel Adaptive Deceleration (260):	1.000000
	Device Accel Velocity Scaling (261):	10.000000
```

the **autogenerated 70-wizardpen.conf** is:
```
Section "InputClass"
   Identifier "wizardpen"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/event*"
   MatchTag "wizardpen"
   Driver "wizardpen"
   Option		"TopX"		"1506"
   Option		"TopY"		"2705"
   Option		"BottomX"	"31225"
   Option		"BottomY"	"30892"
EndSection
```



**What happen when I re-plug the tablet**
```
[  7022.453] (II) config/udev: Adding input device UC-LOGIC Tablet WP5540U (/dev/input/mouse2)
[  7022.453] (II) No input driver/identifier specified (ignoring)
[  7022.459] (II) config/udev: Adding input device UC-LOGIC Tablet WP5540U (/dev/input/event8)
[  7022.459] (**) UC-LOGIC Tablet WP5540U: Applying InputClass "evdev tablet catchall"
[  7022.459] (**) UC-LOGIC Tablet WP5540U: Applying InputClass "wizardpen"
[  7022.459] (II) Using input driver 'wizardpen' for 'UC-LOGIC Tablet WP5540U'
[  7022.459] (II) Loading /usr/lib/xorg/modules/input/wizardpen_drv.so
[  7022.459] (**) UC-LOGIC Tablet WP5540U: always reports core events
[  7022.459] (**) Option "Device" "/dev/input/event8"
[  7022.459] (--) UC-LOGIC Tablet WP5540U: MaxX:0 MaxY:136156901 MaxZ:1023
[  7022.459] (--) UC-LOGIC Tablet WP5540U: aspect ratio:1.00:1
[  7022.459] (**) UC-LOGIC Tablet WP5540U is in absolute mode
[  7022.459] (II) UC-LOGIC Tablet WP5540U: ScreenX = 1024, ScreenY = 768
[  7022.459] (**) UC-LOGIC Tablet WP5540U: TopX                   = 1506
[  7022.459] (**) UC-LOGIC Tablet WP5540U: TopY                   = 2705
[  7022.459] (**) UC-LOGIC Tablet WP5540U: BottomX                = 31225
[  7022.459] (**) UC-LOGIC Tablet WP5540U: BottomY                = 30892
[  7022.459] (**) UC-LOGIC Tablet WP5540U: TopZ    (min pressure) = 0
[  7022.459] (**) UC-LOGIC Tablet WP5540U: BottomZ (max pressure) = 1023
[  7022.459] (**) UC-LOGIC Tablet WP5540U: always reports core events
[  7022.460] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input16/event8"
[  7022.460] (II) XINPUT: Adding extended input device "UC-LOGIC Tablet WP5540U" (type: WizardPen Tablet)
[  7022.461] (II) UC-LOGIC Tablet WP5540U Increment: 1
[  7022.461] (**) UC-LOGIC Tablet WP5540U: (accel) keeping acceleration scheme 1
[  7022.461] (**) UC-LOGIC Tablet WP5540U: (accel) acceleration profile 0
[  7022.461] (**) UC-LOGIC Tablet WP5540U: (accel) acceleration factor: 2.000
[  7022.461] (**) UC-LOGIC Tablet WP5540U: (accel) acceleration threshold: 4
[  7022.470] (II) config/udev: Adding input device UC-LOGIC Tablet WP5540U (/dev/input/mouse3)
[  7022.470] (II) No input driver/identifier specified (ignoring)
[  7022.475] (II) config/udev: Adding input device UC-LOGIC Tablet WP5540U (/dev/input/event9)
[  7022.475] (**) UC-LOGIC Tablet WP5540U: Applying InputClass "evdev pointer catchall"
[  7022.475] (**) UC-LOGIC Tablet WP5540U: Applying InputClass "evdev tablet catchall"
[  7022.475] (**) UC-LOGIC Tablet WP5540U: Applying InputClass "wizardpen"
[  7022.475] (II) Using input driver 'wizardpen' for 'UC-LOGIC Tablet WP5540U'
[  7022.475] (II) Loading /usr/lib/xorg/modules/input/wizardpen_drv.so
[  7022.475] (**) UC-LOGIC Tablet WP5540U: always reports core events
[  7022.475] (**) Option "Device" "/dev/input/event9"
[  7022.475] (--) UC-LOGIC Tablet WP5540U: MaxX:136228805 MaxY:2 MaxZ:0
[  7022.475] (--) UC-LOGIC Tablet WP5540U: aspect ratio:0.00:1
[  7022.475] (**) UC-LOGIC Tablet WP5540U is in absolute mode
[  7022.475] (II) UC-LOGIC Tablet WP5540U: ScreenX = 1024, ScreenY = 768
[  7022.475] (**) UC-LOGIC Tablet WP5540U: TopX                   = 1506
[  7022.475] (**) UC-LOGIC Tablet WP5540U: TopY                   = 2705
[  7022.475] (**) UC-LOGIC Tablet WP5540U: BottomX                = 31225
[  7022.475] (**) UC-LOGIC Tablet WP5540U: BottomY                = 30892
[  7022.475] (**) UC-LOGIC Tablet WP5540U: TopZ    (min pressure) = 0
[  7022.475] (**) UC-LOGIC Tablet WP5540U: BottomZ (max pressure) = 0
[  7022.475] (**) UC-LOGIC Tablet WP5540U: always reports core events
[  7022.475] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input17/event9"
[  7022.475] (II) XINPUT: Adding extended input device "UC-LOGIC Tablet WP5540U" (type: WizardPen Tablet)
[  7022.475] (II) UC-LOGIC Tablet WP5540U Increment: 1
[  7022.475] (**) UC-LOGIC Tablet WP5540U: (accel) keeping acceleration scheme 1
[  7022.475] (**) UC-LOGIC Tablet WP5540U: (accel) acceleration profile 0
[  7022.475] (**) UC-LOGIC Tablet WP5540U: (accel) acceleration factor: 2.000
[  7022.475] (**) UC-LOGIC Tablet WP5540U: (accel) acceleration threshold: 4

```



I've also revert back any mod done by me to 10-evdev.conf in order to be sure.

---

### Post by Favux on 2011-06-28
Yep that is a mess.

Hard to believe the hardware has two seperate events.  I've seen that model before and I don't recall that.

So is the kernel exporting two events?  Or do you have two wizardpen.conf's?  Or a wizardpen.conf and wizardpen entries in the xorg.conf?

Don't know what you mean by:
> the autogenerated 70-wizardpen.conf is
Do you mean the one the PPA installs?  That doesn't look like it.  So where is that coming from?

Anyway change it to read:
```
Section "InputClass"
   Identifier "wizardpen"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/event*"
   MatchTag "wizardpen"
   Driver "wizardpen"
EndSection

Section "InputClass"
   Identifier "wizardpen ignore mouse dev"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/mouse*"
   MatchTag "wizardpen"
   Option         	"ignore" 	"true"
EndSection
```
Which is my best recollection of what the default looks like.

I should be easy enough to either match to event 8 or 9 or exclude one of them.  The problem is event numbers can change if you hot plug usb stuff.  So that not be a permanent fix.

---

### Post by alexan on 2011-06-29
I've applied said modification to 70-wizardpen.conf and the cursor sticked on the top-left side of the screen.

So I had to add this
```
   Option		"TopX"		"1506"
   Option		"TopY"		"2705"
   Option		"BottomX"	"31225"
   Option		"BottomY"	"30892"

```


And now my looks 70-wizardpen.conf like this
```
Section "InputClass"
   Identifier "wizardpen"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/event*"
   MatchTag "wizardpen"
   Driver "wizardpen"
   Option		"TopX"		"1506"
   Option		"TopY"		"2705"
   Option		"BottomX"	"31225"
   Option		"BottomY"	"30892"
EndSection

Section "InputClass"
   Identifier "wizardpen ignore mouse dev"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/mouse*"
   MatchTag "wizardpen"
   Option         	"ignore" 	"true"
EndSection
```
In either way (with or without options) my xinput -list show
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; UC-LOGIC Tablet WP5540U                 	id=9	[slave  pointer  (2)]
&#9116;   &#8627; UC-LOGIC Tablet WP5540U                 	id=10	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=12	[slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                   	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                  	id=14	[slave  keyboard (3)]

```

I was thinking, does exist a command that get or shutdown an input device with given id? Like **kill** [id] does for process?

---

### Post by Favux on 2011-06-29
> I was thinking, does exist a command that get or shutdown an input device with given id? Like kill [id] does for process? 
The problem is both devices have the same names.  Maybe something could be done using xinput with the ID #?  See *man xinput*.  But before that try:
```
Section "InputClass"
    Identifier "WizardPen class"
    MatchIsTablet "on"
    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
    MatchDevicePath "/dev/input/event*"
    Driver "wizardpen"
EndSection

Section "InputClass"
    Identifier "WizardPen ignore mouse dev class"
    MatchIsTablet "on"
    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
    MatchDevicePath "/dev/input/mouse*"
    Option "Ignore" "yes"
EndSection
```
First without your coordinates.  Frankly they don't make sense to me.  The TopX&Y should be 0,0 or close to that anyway.  Where is "1506" and "2705" coming from?

---

### Post by alexan on 2011-07-13
I've found the filed [bug](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/277946) of it. Looks like it's a old issue date 2008... so no real hope to see it fixed :\

---

