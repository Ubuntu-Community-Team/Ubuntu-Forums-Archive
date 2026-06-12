---
title: "Wacom driver issue on 13.10 Lenovo x230t"
date: 2013-11-01
forum: Hardware
---

### Post by Valde_91 on 2013-11-01
Hi everybody!

Today I've upgraded from 12.10 --> 13.04 --> 13.10,  via the upgrade utility. The results is that my X230t works quite well on the PC side, but the tablet side has some majors problems. 

One of them is that the tablet recognize the pen and it works, but is not using the wacom driver. So the buttons and the eraser on the pen doesn't work.

The wacom tablet is recognized by lsusb:

```
valde@valde-ThinkPad:~$ lsusb
Bus 002 Device 003: ID 056a:0090 Wacom Co., Ltd TPC90
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 04f2:b2ea Chicony Electronics Co., Ltd Integrated Camera [ThinkPad]
Bus 001 Device 004: ID 0a5c:21e6 Broadcom Corp. BCM20702 Bluetooth 4.0 [ThinkPad]
Bus 001 Device 003: ID 147e:2020 Upek TouchChip Fingerprint Coprocessor (WBF advanced mode)
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Is in the xinput list:
```
valde@valde-ThinkPad:~$ xinput -list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 90 Pen stylus               	id=10	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Wacom ISDv4 90 Pen eraser               	id=14	[slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                   	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Integrated Camera                       	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                  	id=13	[slave  keyboard (3)]

```

And is also list by wacom x driver: 
```
valde@valde-ThinkPad:~$ xsetwacom --list devices
Wacom ISDv4 90 Pen stylus       	id: 10	type: STYLUS    
Wacom ISDv4 90 Pen eraser       	id: 14	type: ERASER    

```

But when I open the System Setting --> Wacom Tablet, I've this message : "No tablet detected: please plug in or turn on your Wacom tablet. 
 
I haven't this issue with 12.10, but I'm an heavy user of the tablet so I really need to solve this, so any suggestion and help are welcome!

Many Thanks, 
Valde_91

---

### Post by Favux on 2013-11-01
Hi Valde_91,

The fact that xsetwacom list is working means you are on the Wacom drivers.  You can verify by checking Xorg.0.log in /var/log.

I do not understand why your tablet isn't recognized in the System Settings Gnome Wacom applet.  It should be matching the data file isdv4-90.tablet in libwacom.  Libwacom is located in /usr/share/.  It says it matches 056a:0090 which is what you see in lsusb.  The file claims the pen has one button and an eraser and the tablet does not have a touch screen.  Is that correct?  Although I noticed the width and height are likely not correct for a Thinkpad X230t.

You can use an xsetwacom script to configure your pen.  A sample script and instructions are available on this [HOW TO]("http://forums.linuxmint.com/viewtopic.php?f=42&t=110408").  More examples on this wiki page:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration)  from:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Main_Page)

---

### Post by Valde_91 on 2013-11-05
Hi Favux!

As always thank you very much for your precisous help. I think that the problem is in the Gnome applet, but at least with your suggestions I get the pen act almost as before. I've started by adapting the file isdv4-90.tablet in Libwacom to match the screen dimension of my x230t:

```

# USB tablet PC models:  Lenovo x230t
#
# stylus with two button and eraser
#
# Screen size 10.9 x 6.1; 12.5" diagonal

[Device]
Name=Wacom ISDv4 90
DeviceMatch=usb:056a:0090;serial:056a:0090
Class=ISDV4
Width=11
Height=6
IntegratedIn=Display;System

[Features]
Stylus=true
Touch=false
Buttons=0

```

Then I've adapted as follows yours x61t script to set the wacom driver properly:

```


## Wacom preferences for Lenovo x230t ##
# 
##Device names and ID numbers from 'xinput --list' entered in a terminal.
#
## In the example both "Device name" and ID # are used.  Note if you use the
## xorg.conf the "Device names" will be stylus, eraser, touch.
#
## If you are hot plugging use "Device name" as ID # can change.
#
## ClickForce changes name to Threshold with xf86-input-wacom 0.10.9 (11-19-10)
## Lucid default - 0.10.5  Maverick default - 0.10.8
#
## Warning:  Changing Mode to either Absolute or Relative in stylus/eraser stops
## the mouse from being able to pull guidelines out of the ruler in Gimp.

## stylus = ID 10 = "Wacom ISDv4 90 Pen stylus"
xsetwacom set "Wacom ISDv4 90 Pen stylus" Suppress "4"  # data pt.s trimmed, default is 4, 0-20
xsetwacom set "Wacom ISDv4 90 Pen stylus" RawSample "2"  # data pt.s filtered, default is 2, 0-100
xsetwacom set "Wacom ISDv4 90 Pen stylus" Threshold "27"  # pressure, default is 27, range is 0-2047
xsetwacom set "Wacom ISDv4 90 Pen stylus" PressureCurve "5 10 90 95" # Bezier curve, default is 0,0,100,100
xsetwacom set "Wacom ISDv4 90 Pen stylus" TabletPCButton "off"  # stylus tip + button, or "off" for hover mode
xsetwacom set "Wacom ISDv4 90 Pen stylus" Mode "Absolute"  # or Relative cursor movement
xsetwacom set "Wacom ISDv4 90 Pen stylus" Button 1 1  # left mouse click
xsetwacom set "Wacom ISDv4 90 Pen stylus" Button 2 3  # right mouse click
xsetwacom set "Wacom ISDv4 90 Pen stylus" Button 3 3  
# coordinates are the same as used for the stylus
# xsetwacom set "Wacom ISDv4 90 Pen stylus" area 0 0 27760 15694 
# Calibrated ones
xsetwacom set "Wacom ISDv4 90 Pen stylus" area 100 221 27669 15696 

## eraser = ID 14 = "Wacom ISDv4 90 Pen eraser"
xsetwacom set "Wacom ISDv4 90 Pen eraser" Suppress "4"  # data pt.s trimmed, default is 4, 0-20
xsetwacom set "Wacom ISDv4 90 Pen eraser" RawSample "2"  # data pt.s filtered, default is 2, 0-100
xsetwacom set "Wacom ISDv4 90 Pen eraser" Threshold "27"  # pressure, default is 27, range is 0-2047
xsetwacom set "Wacom ISDv4 90 Pen eraser" PressureCurve "0 10 90 100" # default is 0,0,100,100
xsetwacom set "Wacom ISDv4 90 Pen eraser" Mode "Absolute"  # or Relative cursor movement
xsetwacom set "Wacom ISDv4 90 Pen eraser" Button 1 1
# coordinates are the same as used for the stylus
# xsetwacom set "Wacom ISDv4 90 Pen stylus" area 0 0 27760 15694 
# Calibrated ones
xsetwacom set "Wacom ISDv4 90 Pen stylus" area 100 221 27669 15696 

## Developed with MES5464 (adapted by Valde_91)

```

And now my pen is working correctely, and I'm trying to fine tune the calibration right now. 

One more time, Thanks for the help!
Valde_91

---

### Post by Favux on 2013-11-05
Hi Valde_91,

Nice work, looking good.

You are probably correct and it is the applet.

One tip.  If you are happy with the driver default there is no need to reapply it with a xsetwacom command.  Just comment that command out.  But keep it in the script so you have a ready reference of the applicable commands.  And remember you can check the driver defaults with a xsetwacom get command.

---

