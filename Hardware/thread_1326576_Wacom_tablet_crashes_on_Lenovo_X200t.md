---
title: "Wacom tablet crashes on Lenovo X200t"
date: 2009-11-14
forum: Hardware
---

### Post by malleefowl on 2009-11-14
Hi,

I am having several problems when trying to use the touchscreen of my new Lenovo X200t

1) The touchscreen  (Wacom serial on ttyS0)  basically works out of the box, but only the functions stylus and eraser, not the touch. I fixed this by manually configuring this with the xorg.conf file from [http://ubuntuforums.org/showthread.php?t=1179961](http://ubuntuforums.org/showthread.php?t=1179961)
But is there a more elegant way to do this? 

2) With this configuration, the touch function works, but reverts the display to relative mode at the first touch event. 

3) Worst and most urgent problem: In _all_ these configuration, the touchscreen produces a chain of errors 
xf86WcmSerialValidate: bad magic at 6 v=91 l=9
xf86WcmSerialValidate: bad magic at 6 v=91 l=9
xf86WcmSerialValidate: bad magic at 6 v=91 l=9
xf86WcmSerialValidate: bad magic at 6 v=91 l=9
xf86WcmSerialValidate: bad magic at 6 v=91 l=9
xf86WcmSerialValidate: bad magic at 6 v=91 l=9
xf86WcmSerialValidate: bad magic at 6 v=91 l=9
xf86WcmSerialValidate: bad magic at 6 v=91 l=9
xf86WcmSerialValidate: bad magic at 6 v=91 l=9
Error reading wacom device : Resource temporarily unavailable

and, as you can tell from the last line, eventually it stops working. Only a restart of the X server helps. 

Any hints on this problem? 

Many thanks in advance,

Friedemann

---

### Post by Favux on 2009-11-14
Hi malleefowl,

Welcome to Ubuntu Forums!

Can you tell me what version of Ubuntu you are using?

Since you have some function out of the box you must be on at least Intrepid and the 10-wacom.fdi is what was giving you the function.  In Jaunty the 10-wacom.fdi should give you touch too.  In Karmic it's 10-linuxwacom.fdi.

You could be having a conflict between the .fdi and xorg.conf.  Besides the xorg.conf you linked to isn't right.  For example you don't need the cursor and pad stuff.  Those are for a Wacom graphics tablet.

Edit:  By any chance do you mean the really brand new Lenovo X200t with mult-touch?  In that case I probably know what's going on.

---

### Post by malleefowl on 2009-11-15
Hi Favux,

thank you very much for your prompt reply!

My Ubuntu version is indeed 9.10, Karmic Koala. Sorry, I forgot to mention this. 

Indeed, I believe I am talking about the brand new X200t with "Lenovo multitouch" (i.e.: pen and finger, but not two fingers). What is your guess about this?

For the xorg.conf: I thought creating an xorg.conf would override the automatic configuration by the .fdi files. Is this wrong?

And, just by curiosity: All documented attempts to solve this problem somehow boil down to modifying .fdi files, which, as I understand, are configuration scripts for HAL. But I heard that with Karmic, Ubuntu abandonned HAL switching to udev. So why do we have to modify HAL scripts at all?

---

### Post by Favux on 2009-11-15
Hi malleefowl,

OK, Karmic.  What executes last is suppose to control and since xorg.conf executes after HAL it should control.  Practically we've found this isn't always true.  The switch from HAL to DeviceKit is basically transparent to us and you still need to configure with .fdi files.  Things have gotten a little more fiddly in Karmic from either the updated Xorg, or the transition from HAL to DeviceKit, or maybe the increased implementation of Upstart.

I think I helped set up your baby brother a week ago.  That was an HP touch only multi-touch, the HP dv3-2250ep.  It has the new Wacom multi-touch screen with the Product ID e2 and I bet you have the e3.  On this [thread]("http://ubuntuforums.org/showthread.php?t=1314869").

So we want to look at "lsusb".  His reported:
```
Bus 008 Device 002: ID 056a:00e2 Wacom Co., Ltd 
```
And probably also your lshal (lshal>lshal.txt).

If so you need to compile one of the 0.8.5-x linuxwacom series because that's the first linuxwacom that has support for your tablet.  The current one just came out, 0.8.5-4.

---

### Post by malleefowl on 2009-11-16
Hi,

it looks like mine is different:

 lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 0a5c:2145 Broadcom Corp. 
Bus 004 Device 002: ID 08ff:2810 AuthenTec, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0bdb:1900 Ericsson Business Mobile Networks BV 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 17ef:480c Lenovo 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

no wacom :(

and indeed, it seems to be a serial one, as lshal says
  	 	 		
[snip...]
udi = '/org/freedesktop/Hal/devices/pnp_WACf00c_serial_platform_0'
  info.callouts.add = {'hal-setup-wacom'} (string list)
  info.capabilities = {'serial', 'input'} (string list)
  info.category = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pnp_WACf00c'  (string)
  info.product = 'PnP Device (WACf00c)'  (string)
  info.subsystem = 'tty'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_WACf00c_serial_platform_0'  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.ForceDevice = 'ISDV4'  (string)
  input.x11_options.Type = 'stylus'  (string)
  linux.device_file = '/dev/ttyS0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'tty'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:0a/tty/ttyS0'  (string)
  serial.device = '/dev/ttyS0'  (string)
  serial.originating_device = '/org/freedesktop/Hal/devices/pnp_WACf00c'  (string)
  serial.port = 0  (0x0)  (int)
  serial.type = 'platform'  (string)
  wacom.types = {'eraser'} (string list)
[snip...]

I did as you suggested. I removed xorg.conf, switching back to HAL, and installed the 0.8.5-4 driver from source. It loads
 lsmod |grep wacom
wacom                  24048  0 

 dmesg | grep wacom
[    7.731724] usbcore: registered new interface driver wacom
[    7.731728] wacom: v1.49-pc-2:USB Wacom Graphire and Wacom Intuos tablet driver

Xorg.0.log:
(II) config/hal: Adding input device PnP Device (WACf00c)
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
        compiled for 1.6.4, module version = 1.0.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 4.0
(II) Wacom driver level: 47-0.8.5-4 $
(EE) PreInit returned NULL for "PnP Device (WACf00c)"
(EE) config/hal: NewInputDeviceRequest failed (8)
(II) config/hal: Adding input device TPPS/2 IBM TrackPoint

However, I cannot see it in xinput --list any more. And, even more daunting, when I run 
wacdump -c serial -f tpc /dev/ttyS0 
I still get a rising figure for "Invalid argument" as soon as I touch the screen.

---

### Post by Favux on 2009-11-16
Hi malleefowl,

Yes, yours is a serial tablet.  Not the E3.  So unfortunately the 0.8.5-4 compile was unnecessary.  Probably part of the problem is you no longer have the 10-linuxwacom.fdi installed.  That's why the linuxwacom driver isn't attaching in Xorg.0.log.

You could try the test serial .fdi attached to the bottom of the HOW TO.  You'd need to add the WACf00c identifier to it.  Or add back the default .fdi.

The wacom.ko is the linuxwacom usb kernel driver/module so it is irrelevant to you.

The lshal is from before you compiled correct?  So that was with the default linuxwacom.fdi.

Are you sure you have touch or multi-touch?

Are you using 64-bit Karmic?

---

### Post by malleefowl on 2009-11-17
Hi Favux,

thanks for all your help!

recompiling the driver may have been unneccessary, but it should not have caused much harm either. It looks to me like at the moment, there are two problems:
* HAL somehow does not manage to configure the X server correctly
* the driver itself does not work with the tablet (judging from the behaviour of wacdump, which should not depend on the configuration of HAL, right?)

For the .fdi, I assume you were refering to 

[http://ubuntuforums.org/attachment.php?attachmentid=135341&d=1257714521](http://ubuntuforums.org/attachment.php?attachmentid=135341&d=1257714521)

I tried it, inserting WACf00c, as you suggested, but still the tablet does not work, and still the X server says
more /var/log/Xorg.0.log
(II) Wacom driver level: 47-0.8.5-4 $
(EE) PreInit returned NULL for "PnP Device (WACf00c)"

so I think I will switch back to the original settings, as you suggested.

The lshal I sent you was from after the compile. Even now (with your .fdi), it reads
udi = '/org/freedesktop/Hal/devices/pnp_WACf00c_serial_platform_0'
  info.callouts.add = {'hal-setup-wacom'} (string list)
  info.capabilities = {'serial', 'input'} (string list)
  info.category = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pnp_WACf00c'  (string)
  info.product = 'PnP Device (WACf00c)'  (string)
  info.subsystem = 'tty'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_WACf00c_serial_platform_0'  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.ForceDevice = 'ISDV4'  (string)
  input.x11_options.Type = 'stylus'  (string)
  linux.device_file = '/dev/ttyS0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'tty'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:0a/tty/ttyS0'  (string)
  serial.device = '/dev/ttyS0'  (string)
  serial.originating_device = '/org/freedesktop/Hal/devices/pnp_WACf00c'  (string)
  serial.port = 0  (0x0)  (int)
  serial.type = 'platform'  (string)
  wacom.types = {'eraser', 'touch'} (string list)

which looks good to me, but why does the X server complain, then ?

I have touch (I can touch with one, but not several fingers). I think this is called touch, not multi-touch, but it should work with the linuxwacom driver.

My Karmic is 32 bit.

---

### Post by Favux on 2009-11-17
Hi malleefowl,

Good, there seems to be a problem with serial tablets and 64-bit Karmic and we don't have to worry about that.

Good to know there's another serial tablet .fdi identifier.  I need to add that to the .fdi.  I didn't realize WACf00c was a serial tablet pc and with touch.  As you noticed it isn't one of the included two in the serial touch subsection.

I agree with you that lshal looks good.  We need to look at more of the Xorg.0.log and hopefully see why the linuxwacom driver isn't attaching.  I'm not so concerned that it returned:
```
(EE) PreInit returned NULL for "PnP Device (WACf00c)"
```
with the 0.8.5-4 linuxwacom because the 0.8.5 series has new layers of Product ID verifications that don't seem quite sorted out yet.  Hopefully that's the problem and not that WACf00c digitizer has been repurposed with a touch screen and that's why the driver isn't attaching.

To uninstall your compiled version you can follow Appendix 4 in the [HOW TO]("http://ubuntuforums.org/showthread.php?t=1038949").  Then use Synaptic to reinstall the two default 0.8.4-1 packages.  That should add the wacom.rules back in udev which may help.  If you want to keep using the serial .fdi you'll have to reinstall it.

Oh, I forgot to mention wacdump doesn't work after X starts.  The Xdriver wacom_drv.so graps it and wacdump can't see it.  You can use xidump as in "xidump stylus".

---

### Post by malleefowl on 2009-11-18
Hi,

these were great comments. I reverted to the original package with synaptic and now I think I begin to understand what is going on. 

The default .fdi does not include touch capability for my tablet. I added it manually
<match key="@info.parent:pnp.id" contains_outof="WACf008;WACf009;WACf00c">
          <!-- Serial tablets with touch capabilities -->
          <append key="wacom.types" type="strlist">touch</append>
        </match>

Now, HAL indeed adds touch capability

lshal.txt: 
```
...
udi = '/org/freedesktop/Hal/devices/pnp_WACf00c_serial_platform_0'
  info.callouts.add = {'hal-setup-wacom'} (string list)
  info.capabilities = {'serial', 'input'} (string list)
  info.category = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pnp_WACf00c'  (string)
  info.product = 'PnP Device (WACf00c)'  (string)
  info.subsystem = 'tty'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_WACf00c_serial_platform_0'  (stri
ng)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.ForceDevice = 'ISDV4'  (string)
  input.x11_options.Type = 'stylus'  (string)
  linux.device_file = '/dev/ttyS0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'tty'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:0a/tty/ttyS0'  (string)
  serial.device = '/dev/ttyS0'  (string)
  serial.originating_device = '/org/freedesktop/Hal/devices/pnp_WACf00c'  (strin
g)
  serial.port = 0  (0x0)  (int)
  serial.type = 'platform'  (string)
  wacom.types = {'eraser', 'touch'} (string list)

udi = '/org/freedesktop/Hal/devices/pnp_WACf00c_serial_platform_0_subdev_0'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pnp_WACf00c_serial_platform_0'  (s
tring)
  info.product = 'PnP Device (WACf00c) touch'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_WACf00c_serial_platform_0_subdev_
0'  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.ForceDevice = 'ISDV4'  (string)
  input.x11_options.Type = 'touch'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_WACf00c_serial_platform_0_subdev'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pnp_WACf00c_serial_platform_0'  (s
tring)
  info.product = 'PnP Device (WACf00c) eraser'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_WACf00c_serial_platform_0_subdev'
  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.ForceDevice = 'ISDV4'  (string)
  input.x11_options.Type = 'eraser'  (string)
...

```


and even the X server attaches, to all three subdevices stylus eraser and touch

```
(II) config/hal: Adding input device PnP Device (WACf00c)
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
        compiled for 1.6.4, module version = 1.0.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 4.0
(II) Wacom driver level: 47-0.8.4-1 $
(**) PnP Device (WACf00c): always reports core events
(**) PnP Device (WACf00c) device is /dev/ttyS0
(**) PnP Device (WACf00c) is in absolute mode
(**) PnP Device (WACf00c): forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) /dev/ttyS0: Tablet PC buttons are on 
(**) Option "BaudRate" "9600"
(**) PnP Device (WACf00c): serial speed 9600
(II) XINPUT: Adding extended input device "PnP Device (WACf00c)" (type: Wacom St
ylus)
(**) Option "Device" "/dev/ttyS0"
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
usbDetect: can not ioctl version
(==) Wacom using pressure threshold of 15 for button 1
(==) Wacom General ISDV4 tablet speed=9600 (38400) maxX=26312 maxY=16520 maxZ=25
5 resX=2540 resY=2540  tilt=disabled
(==) Wacom device "PnP Device (WACf00c)" top X=0 top Y=0 bottom X=26312 bottom Y
=16520 resol X=2540 resol Y=2540
(II) config/hal: Adding input device PnP Device (WACf00c) touch
(**) PnP Device (WACf00c) touch: always reports core events
(**) PnP Device (WACf00c) touch device is /dev/ttyS0
(**) PnP Device (WACf00c) touch is in absolute mode
(**) PnP Device (WACf00c) touch: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) PnP Device (WACf00c) touch: threshold = 15
(**) PnP Device (WACf00c) touch: max x set to 26312 by xorg.conf
(**) PnP Device (WACf00c) touch: max y set to 16520 by xorg.conf
(**) PnP Device (WACf00c) touch: max z = 255
(**) /dev/ttyS0: Touch is enabled 
(**) /dev/ttyS0: Touch capacity is enabled 
(**) Option "BaudRate" "9600"
(**) PnP Device (WACf00c) touch: serial speed 9600
(II) XINPUT: Adding extended input device "PnP Device (WACf00c) touch" (type: Wa
com Touch)
(==) Wacom device "PnP Device (WACf00c) touch" top X=0 top Y=0 bottom X=65536 bo
ttom Y=65536 resol X=6326 resol Y=10076
(II) config/hal: Adding input device PnP Device (WACf00c) eraser
(**) PnP Device (WACf00c) eraser: always reports core events
(**) PnP Device (WACf00c) eraser device is /dev/ttyS0
(**) PnP Device (WACf00c) eraser is in absolute mode
(**) PnP Device (WACf00c) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) PnP Device (WACf00c) eraser: threshold = 15
(**) PnP Device (WACf00c) eraser: max x set to 26312 by xorg.conf
(**) PnP Device (WACf00c) eraser: max y set to 16520 by xorg.conf
(**) PnP Device (WACf00c) eraser: max z = 255
(**) /dev/ttyS0: Touch is enabled 
(**) /dev/ttyS0: Touch capacity is enabled 
(**) Option "BaudRate" "9600"
(**) PnP Device (WACf00c) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "PnP Device (WACf00c) eraser" (type: W
acom Eraser)
(==) Wacom device "PnP Device (WACf00c) eraser" top X=0 top Y=0 bottom X=26312 b
ottom Y=16520 resol X=2540 resol Y=2540
(II) config/hal: Adding input device ThinkPad Extra Buttons


```


xinput is great, too. I can monitor the stylus (which works fine again) and it produces reasonable results. However, if I monitor the touch device, nothing happens, and as soon as I touch the screen, the wacom tablet does not respond any more, independent of what I am monitoring in xidump at this moment. 

Xorg.0.log reads
```
~$ tail /var/log/Xorg.0.log
xf86WcmSerialValidate: bad magic at 6 v=91 l=9
xf86WcmSerialValidate: bad magic at 6 v=91 l=9
xf86WcmSerialValidate: bad magic at 6 v=91 l=9
xf86WcmSerialValidate: bad magic at 6 v=91 l=9
xf86WcmSerialValidate: bad magic at 6 v=91 l=9
xf86WcmSerialValidate: bad magic at 6 v=91 l=9
xf86WcmSerialValidate: bad magic at 6 v=91 l=9
xf86WcmSerialValidate: bad magic at 6 v=91 l=9
xf86WcmSerialValidate: bad magic at 6 v=91 l=9
Error reading wacom device : Success

```

At this point, only a restart of the X server revives the tablet. 

So, this looks to me like the touch function as implemented in the driver somehow does not understand the code sent by the tablet on ttyS0 and gets confused as soon as the tablet sends touch events. 
Might this mean that my tablet is too new to be supported by linuxwacom?

---

### Post by Favux on 2009-11-18
Hi malleefowl,

That could be, I hope not.  I really don't want to try 0.8.5-4 for reasons I mentioned, plus it's broken for rotation.

If we're lucky it may be the baud rate.  The Ubuntu Karmic .fdi has extra lines to reset the baudrate for one tablet which the vanilla linuxwacom .fdi doesn't have.  I don't know why they didn't do that in the upstream 10-Tabletpcs.fdi like they do with other stuff.  See if adapting this works for you by inserting WACf00c with WACf008:
```
        <match key="@info.parent:pnp.id" contains_outof="WACf008;WACf009">
	  <!-- Serial tablets with touch capabilities -->
	  <append key="wacom.types" type="strlist">touch</append>
	</match>
        <match key="@info.parent:pnp.id" contains_outof="WACf008">
          <!-- Serial tablets that operate at higher baud rate -->
          <merge key="input.x11_options.BaudRate" type="string">38400</merge>
       </match>
```
Of course there are a few other baud rates available.

---

### Post by malleefowl on 2009-11-23
I tried that. It does not resolve the problem, but it may hint towards interesting details. 

The setting makes it into Hal, as can be told from lshal
```

udi = '/org/freedesktop/Hal/devices/pnp_WACf00c'
  info.linux.driver = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PnP Device (WACf00c)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_WACf00c'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:0a'  (string)
  pnp.id = 'WACf00c'  (string)
  pnp.serial.irq = 5  (0x5)  (int)
  pnp.serial.port = '0x200'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_WACf00c_serial_platform_0'
  info.callouts.add = {'hal-setup-wacom'} (string list)
  info.capabilities = {'serial', 'input'} (string list)
  info.category = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pnp_WACf00c'  (string)
  info.product = 'PnP Device (WACf00c)'  (string)
  info.subsystem = 'tty'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_WACf00c_serial_platform_0'  (stri
ng)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.BaudRate = '38400'  (string)
  input.x11_options.ForceDevice = 'ISDV4'  (string)
  input.x11_options.Type = 'stylus'  (string)
  linux.device_file = '/dev/ttyS0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'tty'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:0a/tty/ttyS0'  (string)
  serial.device = '/dev/ttyS0'  (string)
  serial.originating_device = '/org/freedesktop/Hal/devices/pnp_WACf00c'  (strin
g)
  serial.port = 0  (0x0)  (int)
  serial.type = 'platform'  (string)
  wacom.types = {'eraser', 'touch'} (string list)

udi = '/org/freedesktop/Hal/devices/pnp_WACf00c_serial_platform_0_subdev_0'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pnp_WACf00c_serial_platform_0'  (s
tring)
  info.product = 'PnP Device (WACf00c) touch'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_WACf00c_serial_platform_0_subdev_
0'  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.ForceDevice = 'ISDV4'  (string)
  input.x11_options.Type = 'touch'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_WACf00c_serial_platform_0_subdev'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pnp_WACf00c_serial_platform_0'  (s
tring)
  info.product = 'PnP Device (WACf00c) eraser'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_WACf00c_serial_platform_0_subdev'
  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.ForceDevice = 'ISDV4'  (string)
  input.x11_options.Type = 'eraser'  (string)

```

However, X resets the baud rate to 9600 for the touch and eraser devices. Maybe this is the core of the problem. 

Xorg.0.log says
```

(II) config/hal: Adding input device PnP Device (WACf00c)
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
        compiled for 1.6.4, module version = 1.0.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 4.0
(II) Wacom driver level: 47-0.8.4-1 $
(**) PnP Device (WACf00c): always reports core events
(**) PnP Device (WACf00c) device is /dev/ttyS0
(**) PnP Device (WACf00c) is in absolute mode
(**) PnP Device (WACf00c): forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) /dev/ttyS0: Tablet PC buttons are on 
(**) Option "BaudRate" "38400"
(**) PnP Device (WACf00c): serial speed 38400
(II) XINPUT: Adding extended input device "PnP Device (WACf00c)" (type: Wacom St
ylus)
(**) Option "Device" "/dev/ttyS0"
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
usbDetect: can not ioctl version
(==) Wacom using pressure threshold of 15 for button 1
(==) Wacom General ISDV4 tablet speed=38400 (38400) maxX=26312 maxY=16520 maxZ=2
55 resX=2540 resY=2540  tilt=disabled
(==) Wacom device "PnP Device (WACf00c)" top X=0 top Y=0 bottom X=26312 bottom Y
=16520 resol X=2540 resol Y=2540
(II) config/hal: Adding input device PnP Device (WACf00c) touch
(**) PnP Device (WACf00c) touch: always reports core events
(**) PnP Device (WACf00c) touch device is /dev/ttyS0
(**) PnP Device (WACf00c) touch is in absolute mode
(**) PnP Device (WACf00c) touch: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) PnP Device (WACf00c) touch: threshold = 15
(**) PnP Device (WACf00c) touch: max x set to 26312 by xorg.conf
(**) PnP Device (WACf00c) touch: max y set to 16520 by xorg.conf
(**) PnP Device (WACf00c) touch: max z = 255
(**) /dev/ttyS0: Touch is enabled 
(**) /dev/ttyS0: Touch capacity is enabled 
(**) Option "BaudRate" "9600"
(**) PnP Device (WACf00c) touch: serial speed 9600
(II) XINPUT: Adding extended input device "PnP Device (WACf00c) touch" (type: Wa
com Touch)
(==) Wacom device "PnP Device (WACf00c) touch" top X=0 top Y=0 bottom X=65536 bo
ttom Y=65536 resol X=6326 resol Y=10076
(II) config/hal: Adding input device PnP Device (WACf00c) eraser
(**) PnP Device (WACf00c) eraser: always reports core events
(**) PnP Device (WACf00c) eraser device is /dev/ttyS0
(**) PnP Device (WACf00c) eraser is in absolute mode
(**) PnP Device (WACf00c) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) PnP Device (WACf00c) eraser: threshold = 15
(**) PnP Device (WACf00c) eraser: max x set to 26312 by xorg.conf
(**) PnP Device (WACf00c) eraser: max y set to 16520 by xorg.conf
(**) PnP Device (WACf00c) eraser: max z = 255
(**) /dev/ttyS0: Touch is enabled 
(**) /dev/ttyS0: Touch capacity is enabled 
(**) Option "BaudRate" "9600"
(**) PnP Device (WACf00c) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "PnP Device (WACf00c) eraser" (type: W
acom Eraser)
(==) Wacom device "PnP Device (WACf00c) eraser" top X=0 top Y=0 bottom X=26312 b
ottom Y=16520 resol X=2540 resol Y=2540

```

Who tells X to use this wrong baud rate setting? Is there any other source of configuration data than HAL?

---

### Post by Favux on 2009-11-23
Hi malleefowl,

I think I know what is going on.  If so we can get it working.  Looking at this German site for the [Thinkpad X200t]("http://www.golem.de/0909/69829.html") it says:  "Das X200t mit Multitouch-Display nutzt hingegen Wacom-Technik und erlaubt die Bedienung mit zwei Fingern."  Two finger touch is one of the new Wacom multi-touch screens.  Based on that I think you may have the E3 after all.

It's possible that the digitizer is serial and the touchscreen is usb.  And that's the problem.  I need to see your entire lshal (lshal>malleefowl_no_lshal.txt) without a Wacom .fdi and then lshal (lshal>malleefowl_default_lshal.txt) with the default wacom.fdi in Karmic.  Just right click on them and Create Archive and use Manage Attachment to post them.  If I'm right, I basically already have a .fdi that may work.

Edit:  Are you still on linuxwacom 0.8.5-4?  You'll need to be if I am right.

---

### Post by Favux on 2009-11-24
Hi malleefowl,

I reviewed your thread again and as far as I can tell it's consistent with my guess above.   A complete lshal(s) would be helpful.

I decided to attach this .fdi, which is a shot in the dark without the lshal's.  But what the hey.  As I mentioned you'll need 0.8.5-4 installed for there to be any chance of the .fdi working.

---

### Post by malleefowl on 2009-11-28
Hi,

thanks for the comments. Attached you find the two lshals, with and without 10-linuxwacom.fdi in place. 

I am sceptical about the theory of serial stylus and usb touch/erase, since xidump shows events for the touch and erase functions, only they do not make sense. 

Do you happen to know whether the serial interface of the wacom tablets is publicly documented? I could look into the linuxwacom driver to find out, why it does not understand the touch / erase input. 

For the moment, I am back to the original Karmic linuxwacom drivers, but I could revert back to 0.8.4-5 if this is neccessary.

---

### Post by Favux on 2009-12-02
Hi malleefowl,

> I am sceptical about the theory of serial stylus and usb touch/erase
I am too now that I've looked at your lshal.
> Do you happen to know whether the serial interface of the wacom tablets is publicly documented?
No, if you find something I'd be interested.  I suspect part of the problem with documentation is there may be some NDA's in play, but I don't know for sure.

I think what I'd try now is the just released 0.8.5-5.  The release notes say:
> November 30, 2009 - Fixed a kernel driver bug for E3. Updated serial ISDv4 support with newer protocol. Support suspend/resume for kernel 2.6.26 and later. Label 0.8.5-5.
At least the updated serial support sounds relevant to your X200t.  Unfortunately like 0.8.5-4 there seems to be a problem with rotation, but getting the digitizer and touch working seem more important right now.

---

### Post by Favux on 2009-12-10
Hi malleefowl,

Linuxwacom 0.8.5-6 just came out.  And it says:
> Support new serial Tablet PCs.
So my guess is your X200t will now work with it!

---

