---
title: "Wacom Touch Tablet pc in HP dv3-2250ep"
date: 2009-11-04
forum: Hardware
---

### Post by myquidproquo on 2009-11-04
Hi!

I'm using linuxwacom beta driver 0.8.5 and I can't make it work in my laptop. 

lsusb:
> Bus 005 Device 002: ID 0458:0036 KYE Systems Corp. (Mouse Systems) Pocket Mouse LE
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 064e:a102 Suyin Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 056a:00e2 Wacom Co., Ltd 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


dmesg | grep wacom
> [   11.971537] usbcore: registered new interface driver wacom
[   11.971542] wacom: v1.49-pc-2:USB Wacom Graphire and Wacom Intuos tablet driver


ls -l /dev/input/by-path:
> total 0
lrwxrwxrwx 1 root root  9 2009-11-04 23:31 pci-0000:00:1d.0-usb-0:1:1.0-event-mouse -> ../event7
lrwxrwxrwx 1 root root  9 2009-11-04 23:31 pci-0000:00:1d.0-usb-0:1:1.0-mouse -> ../mouse1
lrwxrwxrwx 1 root root  9 2009-11-04 23:31 pci-0000:00:1d.3-usb-0:2:1.0-event -> ../event8
lrwxrwxrwx 1 root root 10 2009-11-04 23:31 pci-0000:00:1d.7-usb-0:5:1.0-event -> ../event10
lrwxrwxrwx 1 root root  9 2009-11-04 23:31 platform-i8042-serio-0-event-kbd -> ../event5
lrwxrwxrwx 1 root root 10 2009-11-04 23:31 platform-i8042-serio-1-event-mouse -> ../event11
lrwxrwxrwx 1 root root  9 2009-11-04 23:31 platform-i8042-serio-1-mouse -> ../mouse3
lrwxrwxrwx 1 root root  9 2009-11-04 23:31 platform-lis3lv02d-event-joystick -> ../event9
lrwxrwxrwx 1 root root  6 2009-11-04 23:31 platform-lis3lv02d-joystick -> ../js0


It's not easy to find reviews about the hardware. I believe this laptop model is really new and only available in Europe.

---

### Post by Favux on 2009-11-04
Hi myquidproquo,

Good.  It's like I thought.  These are the Wacom sections.  Just open the lshal.txt in gedit and search wacom.
```
udi = '/org/freedesktop/Hal/devices/usb_device_56a_e2_noserial'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_3'  (string)
  info.product = 'ISD-V4'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_e2_noserial'  (string)
  info.vendor = 'Wacom Co., Ltd'  (string)
  linux.device_file = '/dev/bus/usb/008/002'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb8/8-2'  (string)
  usb_device.bus_number = 8  (0x8)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.configuration_value = 1  (0x1)  (int)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 3329  (0xd01)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 2  (0x2)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb8/8-2'  (string)
  usb_device.max_power = 0  (0x0)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_interfaces = 1  (0x1)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = 'ISD-V4'  (string)
  usb_device.product_id = 226  (0xe2)  (int)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'Wacom Co., Ltd'  (string)
  usb_device.vendor_id = 1386  (0x56a)  (int)
  usb_device.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_56a_e2_noserial_if0'
  info.linux.driver = 'wacom'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_56a_e2_noserial'  (string)
  info.product = 'USB HID Interface'  (string)
  info.subsystem = 'usb'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_e2_noserial_if0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb8/8-2/8-2:1.0'  (string)
  usb.bus_number = 8  (0x8)  (int)
  usb.can_wake_up = true  (bool)
  usb.configuration_value = 1  (0x1)  (int)
  usb.device_class = 0  (0x0)  (int)
  usb.device_protocol = 0  (0x0)  (int)
  usb.device_revision_bcd = 3329  (0xd01)  (int)
  usb.device_subclass = 0  (0x0)  (int)
  usb.interface.class = 3  (0x3)  (int)
  usb.interface.number = 0  (0x0)  (int)
  usb.interface.protocol = 0  (0x0)  (int)
  usb.interface.subclass = 0  (0x0)  (int)
  usb.is_self_powered = true  (bool)
  usb.linux.device_number = 2  (0x2)  (int)
  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb8/8-2/8-2:1.0'  (string)
  usb.max_power = 0  (0x0)  (int)
  usb.num_configurations = 1  (0x1)  (int)
  usb.num_interfaces = 1  (0x1)  (int)
  usb.num_ports = 0  (0x0)  (int)
  usb.product = 'USB HID Interface'  (string)
  usb.product_id = 226  (0xe2)  (int)
  usb.speed = 12.0 (12) (double)
  usb.vendor = 'Wacom Co., Ltd'  (string)
  usb.vendor_id = 1386  (0x56a)  (int)
  usb.version = 1.1 (1.1) (double)

udi = '/org/freedesktop/Hal/devices/usb_device_56a_e2_noserial_if0_logicaldev_input'
  info.capabilities = {'input', 'input.tablet'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_56a_e2_noserial_if0'  (string)
  info.product = 'Wacom ISDv4 E2'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_e2_noserial_if0_logicaldev_input'  (string)
  input.device = '/dev/input/event8'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_56a_e2_noserial_if0'  (string)
  input.product = 'Wacom ISDv4 E2'  (string)
  input.x11_driver = 'evdev'  (string)
  linux.device_file = '/dev/input/event8'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb8/8-2/8-2:1.0/input/input8/event8'  (string)
```
Try changing:
```
<match key="input.originating_device" contains="if1">
```
to
```
<match key="input.originating_device" contains="if0"
```
You should probably remove the coordinates too.  Those are for gali98's TX2000 tablet pc.  Then see what:
```
xinput --list
```
returns.  If you see touch then try:
```
xsetwacom list
```
If you again see touch then you may be able to use wacomcpl to calibrate.  See "Section 3: Calibrating your Tablet PC" in this [HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

---

### Post by Ayuthia on 2009-11-04
Based on your lshal info:
```
udi = '/org/freedesktop/Hal/devices/usb_device_56a_e2_noserial_if0_logicaldev_input'
  info.capabilities = {'input', 'input.tablet'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_56a_e2_noserial_if0'  (string)
  info.product = 'Wacom ISDv4 E2'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_e2_noserial_if0_logicaldev_input'  (string)
  input.device = '/dev/input/event8'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_56a_e2_noserial_if0'  (string)
  input.product = 'Wacom ISDv4 E2'  (string)
  input.x11_driver = 'evdev'  (string)
  linux.device_file = '/dev/input/event8'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb8/8-2/8-2:1.0/input/input8/event8'  (string)

```The device is assigned to evdev instead of wacom.  It looks like the information in the .fdi file is not making it to X.

Can you post your /usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi file?

Also, before you installed 0.8.5 (is it 0.8.5 or 0.8.5-1?), did you remove the current wacom package:
```
sudo apt-get purge xserver-xorg-wacom
```

EDIT:  It looks like Favux beat me.

---

### Post by myquidproquo on 2009-11-04
Ok. Changed to if0. Now my 10-linuxwacom.fdi file looks like this:
> <?xml version="1.0" encoding="ISO-8859-1"?>
<!-- this is probably a bit imprecise -->
<deviceinfo version="0.2">
  <device>
    <match key="input.originating_device" contains="if0">
	<match key="info.product" contains="Wacom">
		<merge key="input.x11_driver" type="string">wacom</merge>
		<merge key="input.x11_options.Type" type="string">touch</merge>
		<merge key="info.product" type="string">touch</merge>
	</match>
    </match>
  </device>
</deviceinfo>


Running the commands xinput --list:
> "Virtual core pointer"	id=0	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
"Virtual core keyboard"	id=1	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"HP Webcam"	id=2	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Power Button"	id=3	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Power Button"	id=4	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"AT Translated Set 2 keyboard"	id=5	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Sleep Button"	id=6	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Video Bus"	id=7	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Macintosh mouse button emulation"	id=8	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 5
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"SynPS/2 Synaptics TouchPad"	id=9	[XExtensionPointer]
	Type is TOUCHPAD
	Num_buttons is 12
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 1472
		Max_value is 5472
		Resolution is 1
	Axis 1 :
		Min_value is 1408
		Max_value is 4448
		Resolution is 1
"touch"	id=10	[XExtensionKeyboard]
	Type is Wacom Touch
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 5
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 2985
		Resolution is 116
	Axis 1 :
		Min_value is 0
		Max_value is 1687
		Resolution is 105
	Axis 2 :
		Min_value is 0
		Max_value is 255
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"Genius       NetScroll+Mini Traveler"	id=11	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 7
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1


and xsetwacom list:
> touch            touch  

but the touchscreen doesn't respond to my fingers anymore. 
Running wacomcpl I see "touch" there but I get this error:

> can't read "hasTouch(226)": no such element in array
can't read "hasTouch(226)": no such element in array
    while executing
"if { $hasTouch($model) } {
		createPanel 1 0 0 1
	    }"
    (procedure "updateDevice" line 29)
    invoked from within
"updateDevice"
    (command bound to event)

---

### Post by Favux on 2009-11-04
Hi myquidproquo,

Well it looks like things are close to working.  I think the linuxwacom driver has grabbed the device.  My guess it was a mouse .fdi/driver like Synaptics that gave you reaction to touch.

So we need to look at "lshal>lshal.txt" with the new .fdi and Xorg.0.log.


Hi Ayuthia,

I had a head start.  We started on Loic2's Wacom Tablet thread.  This Wacom touch technology may be the same as the Bamboo Pen & Touch is using.  So I was hoping you'd be interested.

---

### Post by myquidproquo on 2009-11-04
To me this is starting to look like serious witchcraft... :P

I really have to learn more about hardware in linux (and linux in general).

---

### Post by Favux on 2009-11-04
Hi myquidproquo,

Looking good.  The lshal looks like the device is being configured correctly by the .fdi/HAL.  The Xorg.0.log shows the linuxwacom driver is grabbing the device:
```
(II) config/hal: Adding input device touch
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Wacom driver level: 47-0.8.4-1 $
(**) touch: always reports core events
(**) touch device is /dev/input/event8
(**) touch is in absolute mode
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) touch: serial speed 9600
(II) XINPUT: Adding extended input device "touch" (type: Wacom Touch)
(**) Option "Device" "/dev/input/event8"
touch Wacom X driver grabbed event device
(==) Wacom using pressure threshold of 15 for button 1
(==) Wacom Unknown USB tablet speed=9600 (38400) maxX=26202 maxY=16325 maxZ=255 resX=1016 resY=1016  tilt=enabled
(==) Wacom device "touch" top X=0 top Y=0 bottom X=2985 bottom Y=1687 resol X=116 resol Y=105
```
This is an important line for you:
```
==) Wacom device "touch" top X=0 top Y=0 bottom X=2985 bottom Y=1687 resol X=116 resol Y=105
```
Since it seems to be giving you your coordinates.

But these lines:
```
(II) Wacom driver level: 47-0.8.4-1 $

==) Wacom Unknown USB tablet speed=9600 (38400) maxX=26202 maxY=16325 maxZ=255 resX=1016 resY=1016  tilt=enabled
```
Seem to suggest linuxwacom 0.8.5-1 isn't correctly installed.  It looks like you still have 0.8.4-1, the Karmic default, or part of it in place.  That may be the problem with wacomcpl also.  So Ayuthia may have hit on part of the problem.  How did you compile and install 0.8.5-1?

Assuming 0.8.5-1 does have support for your touch tablet you may want to install it using this [HOW TO]("http://ubuntuforums.org/showthread.php?t=1038949").  Just change 0.8.4-3 to 0.8.5-1 when you encounter it and use the Karmic step 3).  I'd also install the kernel driver you compile.

Edit:  Using the purge line will remove your 10-linuxwacom.fdi so be prepared to restore it after you're done.

---

### Post by myquidproquo on 2009-11-05
Ok. I guess I'm having some kernel image problem or something like that...

When I compile the 0.8.5-1 driver the files appear in the ./src/2.6.28 folder...I guess they should appear in 2.6.31...

---

### Post by Favux on 2009-11-05
Hi myquidproquo,

No actually that was intentional by Ping at [the LWP]("http://sourceforge.net/mailarchive/forum.php?thread_name=167e8a330910311533t53d4bc18o2c33b60f21620900%40mail.gmail.com&forum_name=linuxwacom-discuss").
> 2.6.31 path was intended for Graphire BlueTooth support (the code for other models are exactly the same as in 2.6.28 ). I found Graphire BlueTooth has been supported in 2.6.31 kernel.org. So there is no need to duplicate the work here.

Ping
So basically starting with 0.8.5 you need to use the Jaunty command to copy the wacom.ko module in place.  Go figure.  I completely forgot about that.  I'll have to add that to the HOW TO.  Thanks for reminding me.

---

### Post by myquidproquo on 2009-11-05
Thanks! :)

It's working now. So I can confirm that Wacom 00e2 works with 0.8.5-1 in this laptop.

Now is it possible to configure advanced control (like zoom or changing workspace with 2 fingers) in Ubuntu?

---

### Post by Favux on 2009-11-05
Hi myquidproquo,

Outstanding!!!  Good work.  You're welcome.

Well Ping is the lead dev. on the LWP so if he says it's supported then it most likely is.  If you haven't already you might want to let him know you got it working in Karmic.

> Now is it possible to configure advanced control (like zoom or changing workspace with 2 fingers) in Ubuntu? 
That's a question for Ayuthia.  I think he might have something.

---

### Post by Ayuthia on 2009-11-05
> **Favux said:**
> Hi myquidproquo,

Outstanding!!!  Good work.  You're welcome.

Well Ping is the lead dev. on the LWP so if he says it's supported then it most likely is.  If you haven't already you might want to let him know you got it working in Karmic.


That's a question for Ayuthia.  I think he might have something.

I have been looking at the 0.8.5-1 code and there is something there for multi-touch, but I have not had a chance to try it out yet.  The feature appears to be built for your laptop though.  I want to say that the feature is automatically turned on for your model, but I could be wrong.  

You might try:
```
xsetwacom set touch Gesture on
```and see if anything changes.
I have not read that far in the code for the gestures yet, but it looks like it sends a triple-tap instead of the one-finger double-tap.  I am just not for sure what gestures it provides though.

---

### Post by myquidproquo on 2009-11-06
I've tried that but I didn't noticed any different behavior.

I'll be making more tests...

---

### Post by Favux on 2009-11-08
Hi myquidproquo and Ayuthia,

For fun check out 23meg's post #9 link 1.  On this [thread]("http://ubuntuforums.org/showthread.php?p=8273199#post8273199").  It's pretty neat.

---

### Post by Ayuthia on 2009-11-08
I was going to play around with XI2 to see how the multi-finger touch works, but the ATI graphics driver is not quite compatible with xorg-server-1.7 yet.  Without the proprietary driver, my laptop fan runs quite a bit.

I did see that other video that 23meg has posted.  It would be nice to either get some better gestures out there or at least do something more with the multi-finger reports.

I have created a simple python script that is able to read the /dev/input/eventX data from my two-finger patch so now I am able to see the X,Y coordinates for two-fingers.  I am trying to figure out how to use it with d-bus just for some fun gestures.

---

### Post by Favux on 2009-11-18
Hi myquidproquo,

I was wondering if you would do me a favor.  I'm trying to develop a wacom.fdi that will work for all (most) of the Wacom tablets.  Your E2 is the only one I know of that puts touch on 'if0' instead of 'if1'.  I've tried to sneak touch for your multi-touch screen into 'if0'.  I'm hoping you'll test the .fdi attached and let me know if it works for you.  I'd really appreciate it.

Edit:  If test3 doesn't work (give you touch) would you please also try test3.2.

---

### Post by myquidproquo on 2009-11-21
I'm sorry,I've just seen this message today.

But I have good news...Version 3 didn't work at all, the cursor didn't respond, but 3.2 works great :)

Any news about multi touch? Should I be waiting for anything really fantastic for the next Ubuntu version? :)

---

### Post by myquidproquo on 2009-11-21
Something like this...
[http://www.youtube.com/watch?v=DTeUbx_nnM4&feature=related](http://www.youtube.com/watch?v=DTeUbx_nnM4&feature=related)

Is this possible?

---

### Post by Ayuthia on 2009-11-21
> **myquidproquo said:**
> Something like this...
[http://www.youtube.com/watch?v=DTeUbx_nnM4&feature=related](http://www.youtube.com/watch?v=DTeUbx_nnM4&feature=related)

Is this possible?

If I recall correctly, that is supposed to be able to work with the N-Trig digitizers and the Vista firmware.  I have not tried it in a while though and I am now using the Windows 7 firmware which reports things differently.

If you want to do it with their source code, you will need to have access to the /dev/input/eventX so that you can have access to the X,Y coordinates of the fingers.  From there you can then make d-bus calls to compiz to make it all work.  The Wacom driver blocks out the X,Y information from being read so that is the current hurdle.  That was done so that other hardware drivers (like synaptics or evdev) won't capture the data and use it while the Wacom driver is in use.

I have been thinking of trying it out with mine since I am able to read the two points.  However I did have to create a special driver so that I can read it.

The new XI2 is out so it is supposed to be capable of using multi-finger pointers so it is not too far out.  The main problem is getting the proprietary graphics drivers (ATI and NVidia) to work with the new xorg-server.

---

### Post by Favux on 2009-11-21
Hi myquidproquo,

Outstanding!  Thanks for testing that.  So using the lines in 3.2 we can add support to the E2 to the generic .fdi.  Cool!  I wonder if the E3 sets up the same way?  And what brand and model it's in?

You may have already, but "xinput --list" should just show touch with 3.2.  And "xsetwacom list" and wacompl should also just have touch.

Ayuthia, ob1kenobe, and prefiks2 are looking at two finger touch gestures in the linuxwacom 0.8.5-4 code right now.  So there may something to report shortly.

---

### Post by dumathor on 2009-11-23
Hi myquidproquo,

I have almost the same notebook as you, mine is the dv3 2240ez. I tried to follow this thread along with the wacom install howto from Favux to get the touch screen running on my Karmic 2.6.31-14-generic-pae.

My question would be if you added a new symlink to the 40-xserver-xorg-input-wacom.rules in order to assign the Wacom E2 touch screen to the wacom module. 

Mine gets assigned to "Synaptics" regardless of what I do:

```

udi = '/org/freedesktop/Hal/devices/usb_device_56a_e2_noserial_if0_logicaldev_input'
  info.callouts.add = {'hal-setup-wacom'} (string list)
  info.capabilities = {'input', 'input.touchpad'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_56a_e2_noserial_if0'  (string)
  info.product = 'touch'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_56a_e2_noserial_if0_logicaldev_input'  (string)
  input.device = '/dev/input/event10'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_56a_e2_noserial_if0'  (string)
  input.product = 'Wacom ISDv4 E2'  (string)
  input.x11_driver = 'synaptics'  (string)
  input.x11_options.Type = 'touch'  (string)
  linux.device_file = '/dev/input/event10'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.3/usb8/8-2/8-2:1.0/input/input10/event10'  (string)
  wacom.types = {'eraser', 'cursor', 'pad'} (string list)

```

Everything looks similar to your output until I get to xinput --list, which is just missing the touch entry, most probably because Synaptics is grabbing the whole thing.

---

### Post by Favux on 2009-11-23
Hi dumathor,

Welcome to Ubuntu Forums!

We could construct a symlink and see if that works.

Or we could try altering the Synaptic .fdi so it isn't so grabby.  If you want to go that route try nesting a second set of match lines for the Synaptic .fdi.  It's called "11-x11-synaptics.fdi" and it's located at "/usr/share/hal/fdi/policy/20thirdparty/".  Add:
```
    <match key="info.product" contains="Synaptics">

    </match>
```
So it looks like:
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
    <match key="info.product" contains="Synaptics">

......

    </match>
    </match>
  </device>
</deviceinfo>
```
We should really look at the Synaptic section(s) in your lshal, but I think that will work.

I'd use:
```
gksudo gedit /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi
```
to edit, and then reboot.

---

### Post by dumathor on 2009-11-23
Yup, that was it. I did not even think about restricting the Synaptics fdi but had my mind only on the wacom one :)

The touch screen works now after the reboot. If you want me to test out anything else for this notebook I'll be more than glad to help out.

Cheers

---

### Post by Favux on 2009-11-23
Hi dumathor,

Good, glad that worked!  So you are using linuxwacom 0.8.5-4?

> If you want me to test out anything else for this notebook I'll be more than glad to help out.
In fact I do have a new generic .fdi that I think I've worked the kinks out of.  I'd love to have you test it.  It's located [here]("http://ubuntuforums.org/showpost.php?p=8367378&postcount=579").

What I'd like is pre and post lshal>dumathor_pre-lshal.txt (and similar with post).  Hopefully touch will work for you and "xsetwacom list" and wacomcpl will only show touch for you.  If not let me know what you see.  I'd really appreciate the favor.

---

### Post by dumathor on 2009-11-23
Favux,

Actually I already use that fdi :)

I tried it out while searching for the reason the touch screen was not recognised and I did not switch it back to the original fdi

Anyway, I've attached the output from lshal

Edit: I've just attached the pre-lshal coming from the original fdi of the 0.8.5-4 package. With this one the touch screen does not work.

---

### Post by Favux on 2009-11-23
Hi dumathor,

> Actually I already use that fdi
lol  :p

From the lshal in "xsetwacom list" and wacomcpl you should only be seeing touch.  Is this correct?

Edit:  Thanks for adding the pre-lshal, that confirms what I suspected/was pretty sure of.  Touch won't work added as an append on an info.callout for usb.

---

### Post by dumathor on 2009-11-23
Nope, on xsetwacom list I see

```
touch   touch
```

wacomcpl gives me only 

```
touch
```


On Xorg.0 I can see:

```
(II) config/hal: Adding input device touch
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Wacom driver level: 47-0.8.5-4 $
(**) touch: always reports core events
(**) touch device is /dev/input/event10
(**) touch is in absolute mode
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) touch: serial speed 9600
(II) XINPUT: Adding extended input device "touch" (type: Wacom Touch)
(**) Option "Device" "/dev/input/event10"
touch Wacom X driver grabbed event device
(**) /dev/input/event10: Touch is enabled 
(**) /dev/input/event10: Touch Gesture is enabled 
(==) Wacom using pressure threshold of 15 for button 1
(==) Wacom USB TabletPC tablet speed=9600 (38400) maxX=0 maxY=0 maxZ=255 resX=10 resY=10  tilt=disabled
```

---

### Post by Favux on 2009-11-23
Hi dumathor,

That's perfect.  That's what you should be seeing.  The double touch in "xsetwacom list" is I think something they're trying to get rid of in the 0.8.5 code.

Out of curiosity does touch in wacomcpl offer you the option to calibrate touch?

I wish an E3 would show up so we could see how it sets up.  I'm wondering if it is the same as the E2 or does it have a stylus?  Actually what I've been wondering is if it is the Lenovo T400s?

---

### Post by dumathor on 2009-11-23
Yes I am able to calibrate the touchscreen without a problem. 

What device would have an E3 in it? While I was looking around for my problems the only recently introduced touchscreen hardware from Wacom I found was the E3. And the T400s is based on an N-Rig panel according to this page here:

[http://www.golem.de/0909/69829.html](http://www.golem.de/0909/69829.html)

(sorry, it is in German :D )

The X200t seems to have a Wacom touchscreen though according to this thread here: [http://ubuntuforums.org/showthread.php?p=8343507](http://ubuntuforums.org/showthread.php?p=8343507)

---

### Post by Favux on 2009-11-23
Hi dumathor,

Sehr gut, an N-trig duosense for the T400s.  I wonder if it is the new one or the same one as in the Dell XT and XT2 and HP TX2z?

The X200t has a Wacom serial digitizer with a touchscreen.

So we still don't know what has the E3.

Ah:  Das X200t mit Multitouch-Display nutzt hingegen Wacom-Technik und erlaubt die Bedienung mit zwei Fingern.  That sounds like the E3 maybe.  And that might be why the new X200t I was trying to set up wouldn't work.  It used a different serial identifier for the digitizer.  If it has the E3 touchscreen in addition that was the problem, and why it wouldn't work.  So could the touchscreen be on usb and the digitizer still serial?  That would be weird.

---

### Post by dumathor on 2009-11-24
One more thing Favux:

To solve the problem on my dv3 that the touchscreen was not detected by the wacom module we did change the Synaptics fdi file. 

I think this problem will appear for all notebooks that have this particular combination of Synaptics touchpad and Wacom touchscreen. Wouldn't it be better to alter the wacom fdi to fix the recognition of the touchscreen? With that there will be only one driver module that has to be changed.

If you want to test it I would help you with that.

---

### Post by Favux on 2009-11-24
Hi dumathor,

Thank you for the offer.  I'll take you up on that.  I'm about ready to post a new generic Wacom.fdi that will hopefully work for almost everyone.  The holiday will probably interrupt that.

I empirically know from many testers that the basic match lines I use work for USB Wacom.  It would be hard to duplicate that many testers (at least 760 now).  I think the problem is with the Synaptic .fdi.  For example it can grab the N-trig digitizer/touchscreen too.  It was grabbing the new Wacom P & T's we are working on.  And it wouldn't surprise me if it grabs other touchscreens.  So I think the Synaptic .fdi is what needs to be fixed.

Edit:  By the way it's been a long standing problem.  With Intrepid and earlier we had to change the name from TouchPad to Pad in the Synaptic device section and ServerLayout so it wouldn't grab our touchscreen.  I gather whoever writes the Synaptic .fdi does not have a Wacom or similar device.  :)

---

### Post by myquidproquo on 2009-11-25
Hi everyone...

I'm again with no touchscreen. I guess that this is since the last ubuntu update...

---

### Post by Favux on 2009-11-25
Hi myquidproquo,

If there was a kernel update you probably have to recompile linuxwacom.  You could first try recopying the wacom.ko from your previous compile into place using the copy command in the HOW TO (the new kernel's number will be added and so it goes to a different location).  With luck that will work.

Otherwise see if it's what happened with dumather in post #21.  Check "xinput --list", Xorg.0.log, or your lshal and see if the Synaptic touchpad .fdi is grabbing your touchscreen.  If it is you can try the solution in post #22.

---

### Post by mcoleman44 on 2010-02-09
Hi favux!

Here is my 11-x11-synaptics.fdi

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
    <match key="info.product" contains="synaptics">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <!-- Arbitrary options can be passed to the driver using
             the input.x11_options property since xorg-server-1.5. -->
        <!-- EXAMPLE:
        <merge key="input.x11_options.LeftEdge" type="string">120</merge>
        -->
    </match>
    </match>    
  </device>
</deviceinfo>
```

Is this right?

---

### Post by Favux on 2010-02-09
Hi mcoleman44,

The Synaptic .fdi looks right.

Looking at your lshal I'm seeing the linuxwacom driver attaching to your n-trig.  That suggests the problem is with your 10-wacom.fdi.  Did you comment out the n-trig part like "2) Commenting out the N-trig subsection of 10-wacom.fdi" in the HOW TO shows you?

---

### Post by mcoleman44 on 2010-02-09
If I did this I dont remember doing it. Is that what I need to do? Here is my 10-wacom.fdi:

```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->

<deviceinfo version="0.2">
  <device>
    <match key="info.category" contains="input">
      <match key="info.product" contains="Wacom">
    <merge key="input.x11_driver" type="string">wacom</merge>
    <merge key="input.x11_options.Type" type="string">stylus</merge>
        <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
        <append key="wacom.types" type="strlist">eraser</append>
        <append key="wacom.types" type="strlist">cursor</append>
        <append key="wacom.types" type="strlist">pad</append>
      </match>
      <match key="info.product" contains="WALTOP">
    <merge key="input.x11_driver" type="string">wacom</merge>
    <merge key="input.x11_options.Type" type="string">stylus</merge>
        <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
        <append key="wacom.types" type="strlist">eraser</append>
        <append key="wacom.types" type="strlist">cursor</append>
        <append key="wacom.types" type="strlist">pad</append>
      </match>
    </match>
    <match key="info.capabilities" contains="serial">
      <match key="@info.parent:pnp.id" contains_outof="WACf001;WACf002;WACf003;WACf004;WACf005;WACf006;WACf007;WACf008;WACf009;WACf00a;WACf00b;WACf00c;FUJ02e5">
        <append key="info.capabilities" type="strlist">input</append>
        <merge key="input.x11_driver" type="string">wacom</merge>
        <merge key="input.x11_options.Type" type="string">stylus</merge>
        <merge key="input.x11_options.ForceDevice" type="string">ISDV4</merge>
        <merge key="input.device" type="copy_property">serial.device</merge>
        <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
        <append key="wacom.types" type="strlist">eraser</append>
        <match key="@info.parent:pnp.id" contains_outof="WACf008;WACf009">
          <!-- Serial tablets with touch capabilities -->
          <append key="wacom.types" type="strlist">touch</append>
        </match>
      </match>
    </match>
    <!-- N-Trig Duosense Electromagnetic Digitizer -->
    <match key="info.product" contains="HID 1b96:0001">
      <match key="info.parent" contains="if0">
       <merge key="input.x11_driver" type="string">wacom</merge>
       <merge key="input.x11_options.Type" type="string">stylus</merge>
      </match>
    </match>
  </device>
  <!-- Match the Wacom Bluetooth A5 pen tablet -->
  <device>
    <match key="info.capabilities" contains="input.mouse">
      <match key="info.product" contains="WACOM">
        <match key="info.product" contains="Tablet">
          <merge key="input.x11_driver" type="string">wacom</merge>
          <merge key="input.x11_options.Type" type="string">stylus</merge>
          <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
          <append key="wacom.types" type="strlist">eraser</append>
          <append key="wacom.types" type="strlist">cursor</append>
        </match>
      </match>
    </match>
  </device>

</deviceinfo>
```

---

### Post by Favux on 2010-02-09
Yep, that may be it.  If you reinstalled wacom-tools it'll replace the .fdi.  That may be what happened.

---

### Post by mcoleman44 on 2010-02-09
Ok, i commented out the n-trig subsection. Problem is... my mouse pad wont work. when i touch the screen, the cursor still goes to the top left corner.

---

### Post by Favux on 2010-02-09
Alright.  I'm not sure why you've lost touchpad function, that shouldn't happen.  You can remove your changes to the Synaptic .fdi and see if that helps.

Why would you be trying touch?  I thought the point was to remove it and we did?  Are you saying your stylus doesn't work either now?

If so I think what is going on is the only reason you saw any function was you had the basic support Jaunty offers to n-trig out of the box with the default wacom.fdi and the default Jaunty linuxwacom (which is specially patched and not the standard 0.8.2-2).  That means you have none of the kernel support from Ayuthia's patches.

So you need to reread and go over everything because you're misunderstanding something fundamental.  I think you can do it because you've already learned a lot.

In the meantime remove the comment from the n-trig section in the wacom.fdi.  Restore it to the way it was in other words.  Then go ahead and make your xorg.conf back to normal, i.e. pre-wacom entries.  That should give you basic stylus function without touch.

---

### Post by Favux on 2010-02-09
Since the current Ayuthia kernel deb.s are for kernel  2.6.28-16-generic let's see if we can get him or someone to compile some new deb.s for 2.6.28-18-generic.  Is that the latest Jaunty kernel?  How long ago did that come through, do you know?  Also check with Update Manager that there isn't a newer kernel.

---

### Post by mcoleman44 on 2010-02-09
You caught me red-handed! That is the reason i chose Jaunty. And we were trying to get touch to stop working, but we hadn't succeeded yet. Im trying to turn off touch completley, and i was just checking to see if it had worked. but it didnt. Instead of turning off touch iit turned off the touchpad. Not so sure why tho. And I have learned a lot, thanks to you.

---

### Post by mcoleman44 on 2010-02-09
Yes, that is the latest version. In the meantime can i just downgrade my kernel and use his deb's?

---

### Post by Favux on 2010-02-09
Yes!!!

---

### Post by M42 on 2010-02-15
> **Favux said:**
> Hi dumathor,

I wish an E3 would show up so we could see how it sets up.  I'm wondering if it is the same as the E2 or does it have a stylus?  Actually what I've been wondering is if it is the Lenovo T400s?

Favux,

If you are still looking for a an e3, this post
 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/516777](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/516777)

in launchpad seems to indicate that the e3 is in the new HP tm2t tablet.

M42

---

### Post by Favux on 2010-02-15
Hi M42,

Cool!  So the E3 is the HP TM2.

Thanks for that!  I've been toying with the idea of getting one.  Especially since HP went back to Wacom.  Not sure if I like the idea of no internal DVD though.  If you buy an external it'd be tough to justify upgrading to the add-in ATI video.  It'd be easier if it was an Nvidia add-in.  Not sure if I could survive on the internal Intel though.

---

### Post by M42 on 2010-02-15
> **Favux said:**
> Hi M42,

Cool!  So the E3 is the HP TM2.

Thanks for that!  I've been toying with the idea of getting one.  Especially since HP went back to Wacom.  Not sure if I like the idea of no internal DVD though.  If you buy an external it'd be tough to justify upgrading to the add-in ATI video.  It'd be easier if it was an Nvidia add-in.  Not sure if I could survive on the internal Intel though.

I've been think about getting the tm2 also but have some of the same concerns you have.  I really like the 9 hour (maybe) battery life and the cool running processors. I don't need the ATI graphics but would like to have the 1.6 Ghz processor since the 1.6 seems to have an equivalent processing capability as the Tx2000.  I rarely use the internal DVD in the Tx2000 and have started using the USB disk approach to install a new operating environment so not having an internal drive is not a big concern for me.  

By the way thanks again for all your help, as well as the help of other on the forums, getting my tx2000 working great in tablet mode.

M42

---

### Post by Favux on 2010-02-15
Hi M42,

Thanks for the thanks!  :)

Good points.  I've been wondering about the ULV dual core CPU's.  Can you cite something showing equivalence to the TX2000's AMD's or is that your feel/guess from looking at stuff?  Cause the AMD's are fine for me.  So if they are the equivalent no worries.

Good point on usb install!

---

### Post by M42 on 2010-02-15
> **Favux said:**
> Hi M42,

Thanks for the thanks!  :)

Good points.  I've been wondering about the ULV dual core CPU's.  Can you cite something showing equivalence to the TX2000's AMD's or is that your feel/guess from looking at stuff?  Cause the AMD's are fine for me.  So if they are the equivalent no worries.

Good point on usb install!

This 

[http://forum.tabletpcreview.com/forumdisplay.php?f=1039&order=desc](http://forum.tabletpcreview.com/forumdisplay.php?f=1039&order=desc)

is a forum that has a lot of posts from people that have purchased the tm2 and their experiences.  One of the of the posts, I don't remember which one, had a screen shot of his windows experience numbers that show the 1.6 Ghz tm2 to have a number of 4.8 for the processor calculations per second.  That is the same number my tx2000 shows when I run display the windows experience window.

---

### Post by Favux on 2010-02-15
Thanks for the info.!  I'll look it over.

---

### Post by M42 on 2010-02-15
Favux, 
Found the post I mentioned above. 
[http://forum.tabletpcreview.com/showthread.php?t=30467](http://forum.tabletpcreview.com/showthread.php?t=30467)
It is several posts into this thread.
M42

---

