---
title: "Trouble with ActionStar touch screen tablet &amp; EvTouch"
date: 2011-03-31
forum: Hardware
---

### Post by age6racer on 2011-03-31
Hi all,

I'm hoping someone else is struggling with this same hardware.

Here is what I have been able to find out about the hardware I have so far...

With stock Ubuntu install (no new drivers or fiddling from me) I found that the screen behaved basically as a big left-mouse-button. If I positioned the cursor (using a mouse) over a button of link and then touched the screen it would register the click. I also found that if I touched the screen once the cursor wouldn't move but if I touched it in a second location while holding my first finger on the screen then the cursor would jump to the second touch point.

I figured out that the screen is by ActionStar. It is listed on [ENAC's website]("http://lii-enac.fr/en/architecture/linux-input/multitouch-devices.html") as a work in progress. This is my lsusb output.

```
lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 2101:1011 ActionStar 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0461:4d61 Primax Electronics, Ltd 
Bus 002 Device 002: ID 04d9:1605 Holtek Semiconductor, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 1e4e:0102  
Bus 001 Device 005: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 001 Device 003: ID 13d3:3273 IMC Networks 802.11 n/g/b Wireless LAN USB Mini-Card
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

The output of "xinput --list" showed a device named "NAS 10.1" I Googled and found the following page.. [http://askubuntu.com/questions/16458/multitouch-screen-needs-two-touch-points]("http://askubuntu.com/questions/16458/multitouch-screen-needs-two-touch-points")

I installed the ENAC drivers and the NAS 10.1 entry disappeared from the xinput output.

I then followed the steps to add my device from the userspace.

Now the output of xinput looks like this.

```
xinput -list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; EVTouch TouchScreen                     	id=12	[slave  pointer  (2)]
&#9116;   &#8627; HP HP Wireless Comfort Mouse            	id=17	[slave  pointer  (2)]
&#9116;   &#8627; EVTouch TouchScreen                     	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627;   USB Keyboard                          	id=10	[slave  keyboard (3)]
    &#8627;   USB Keyboard                          	id=11	[slave  keyboard (3)]
    &#8627; USB2.0 Camera                           	id=14	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=15	[slave  keyboard (3)]
    &#8627; Topstar Laptop extra buttons            	id=16	[slave  keyboard (3)]

```

and the EvTouch entries..

```
  &#8627; EVTouch TouchScreen                     	id=12	[slave  pointer  (2)]
	Reporting 3 classes:
		Class originated from: 12
		Buttons supported: 5
		Button labels: Button Left Button Middle Button Right Button Wheel Up Button Wheel Down
		Button state:
		Class originated from: 12
		Detail for Valuator 0:
		  Label: None
		  Range: 0.000000 - 1024.000000
		  Resolution: 1024 units/m
		  Mode: absolute
		  Current value: 1023.000000
		Class originated from: 12
		Detail for Valuator 1:
		  Label: None
		  Range: 0.000000 - 600.000000
		  Resolution: 1024 units/m
		  Mode: absolute
		  Current value: 599.000000

&#9116;   &#8627; HP HP Wireless Comfort Mouse            	id=17	[slave  pointer  (2)]
	Reporting 3 classes:
		Class originated from: 17
		Buttons supported: 13
		Button labels: Button Left Button Middle Button Right Button Wheel Up Button Wheel Down Button Horiz Wheel Left Button Horiz Wheel Right Button Side Button Extra Button Unknown Button Unknown Button Unknown Button Unknown
		Button state:
		Class originated from: 17
		Detail for Valuator 0:
		  Label: Abs X
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative
		Class originated from: 17
		Detail for Valuator 1:
		  Label: Abs Y
		  Range: -1.000000 - -1.000000
		  Resolution: 1 units/m
		  Mode: relative

&#9116;   &#8627; EVTouch TouchScreen                     	id=13	[slave  pointer  (2)]
	This device is disabled
	Reporting 3 classes:
		Class originated from: 13
		Buttons supported: 5
		Button labels: Button Left Button Middle Button Right Button Wheel Up Button Wheel Down
		Button state:
		Class originated from: 13
		Detail for Valuator 0:
		  Label: None
		  Range: 0.000000 - 1024.000000
		  Resolution: 1024 units/m
		  Mode: absolute
		  Current value: 512.000000
		Class originated from: 13
		Detail for Valuator 1:
		  Label: None
		  Range: 0.000000 - 600.000000
		  Resolution: 1024 units/m
		  Mode: absolute
		  Current value: 300.000000


```

While following a red-herring from the manufacturers website I wrongfully installed the eGalax drivers and created a new xorg.conf.

```
Section "ServerLayout"
        InputDevice "EETI" "SendCoreEvents"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "glx"
	Load  "record"
	Load  "extmod"
	Load  "dri"
	Load  "dbe"
	Load  "dri2"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	BusID       "PCI:0:2:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

### Touch Configuration Beginning ###
Section "InputDevice"
        Identifier "EETI"
        Driver "egalax"
        Option "Device" "usbauto"
        Option "Parameters" "/var/lib/eeti.param"
        Option "ScreenNo" "0"
EndSection
### Touch Configuration End ###
``` 

I now have a semi-working touch screen. The top left corner of the screen works like a small laptop trackpad. If I move my finger around in the top 2 square inches of the screen I can control the cursor. Clicking doesn't really work as I already have my finger on the screen.

So close but yet so far!

Does any one have any advice as to what I should do next?
Or better still has anyone got one of these screen working yet?

Let me know if you need any more info.
Thanks for reading!

---

### Post by age6racer on 2011-03-31
Ok some updates.

I have reinstalled the same version of Ubuntu but not installed any updates.

I checked the touch screen straight away and found that I have some tracking of my finger but the cursor will only move vertically and doesn't want to leave the right 1/3 of the screen.

I checked xinput output and lsusb and they were are they were before.

I installed the ENAC drivers and moved them from userspace as before
rebooted and voila! I have fully working finger tracking and clicking on the whole screen.

THEN...

after about 15 seconds the cursor jumps back to the right 1/3 of the screen and I'm back to where I started.

Any ideas now people?

---

### Post by age6racer on 2011-03-31
dmesg | grep HID
[    3.968333] usbhid: USB HID core driver
[    4.017862] hid-multitouch 0003:2101:1011.0001: input,hidraw0: USB HID v1.11 Device [NAS      10.1 ] on usb-0000:00:1d.1-2/input0
[   40.099653] generic-usb 0003:0461:4D61.0002: input,hidraw1: USB HID v1.10 Mouse [HP HP Wireless Comfort Mouse] on usb-0000:00:1d.0-2/input0
[   45.369388] generic-usb 0003:04D9:1605.0003: input,hidraw2: USB HID v1.10 Keyboard [  USB Keyboard] on usb-0000:00:1d.0-1/input0
[   45.474656] generic-usb 0003:04D9:1605.0004: input,hidraw3: USB HID v1.10 Device [  USB Keyboard] on usb-0000:00:1d.0-1/input1

---

### Post by Favux on 2011-03-31
Hi age6racer,

Since the ENAC stuff seems to be putting it on the evtouch driver (or is it a modified version of evtouch?) it seems you may need to add coordinate Options to the evtouch.conf.

---

