---
title: "WALTOP International Corp. Slim Tablet not working..."
date: 2010-01-18
forum: Hardware
---

### Post by michaelcole on 2010-01-18
Howdy, I'm trying to use a "Vistablet" tablet.  It's a waltop/aiptek clone I think.  I can't get it to work though.  Any tips?

Here's what I tried: [https://help.ubuntu.com/community/AiptekTablet](https://help.ubuntu.com/community/AiptekTablet)

What am I doing wrong?
1) plug in tablet
2) $ xinput -list
3) Find the name of tablet: "WALTOP International Corp. Slim Tablet"
4) Check to find your tablet on this list:
    <this is a short list, try this out and add yours if it works>
5) unplug tablet
6) $ sudo aptitude install xserver-xorg-input-aiptek
7) $ sudo nano /usr/share/hal/fdi/policy/10-linuxaiptek.fdi
    Paste this into the file: 
      <?xml version="1.0" encoding="UTF-8"?>
      <deviceinfo version="0.2">
        <device>
          <match key="info.product" contains="WALTOP">
            <merge key="input.x11_driver" type="string">aiptek</merge>
            <merge key="input.x11_options.SendCoreEvents" type="string">true </merge>
            <merge key="input.x11_options.USB" type="string">On</merge>
            <merge key="input.x11_options.Type" type="string">stylus</merge>
            <merge key="input.x11_options.Mode" type="string">absolute</merge>
          </match>
        </device>
      </deviceinfo>
8) Plug in tablet
9) Check install like this:
   Applications -> Graphics -> GIMP
   Edit -> Preferences -> Input Devices -> Configure Extended Input Devices ...

No worky!



More info: 

michael@mc-desktop:~$ dmesg | tail
	...
	[81070.691336] input: WALTOP International Corp. Slim Tablet as /devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4.3/1-4.3:1.0/input/input25
	[81070.691493] generic-usb 0003:172F:0031.0005: input,hidraw3: USB HID v1.10 Mouse [WALTOP International Corp. Slim Tablet] on usb-0000:00:12.2-4.3/input0
	...
	[81835.791575] input: WALTOP International Corp. Slim Tablet as /devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4.3/1-4.3:1.0/input/input26
	[81835.791737] generic-usb 0003:172F:0031.0006: input,hidraw3: USB HID v1.10 Mouse [WALTOP International Corp. Slim Tablet] on usb-0000:00:12.2-4.3/input0

michael@mc-desktop:~$ lsusb
	...
	Bus 001 Device 010: ID 172f:0031  
	...

michael@mc-desktop:~$ xinput -list
	...
	"WALTOP International Corp. Slim Tablet"	id=4	[XExtensionPointer]
		Type is TOUCHPAD
		Num_buttons is 13
		Num_axes is 17
		Mode is Absolute
		Motion_buffer is 256
		Axis 0 :
			Min_value is 0
			Max_value is 10000
			Resolution is 10000
		Axis 1 :
			Min_value is 0
			Max_value is 6250
			Resolution is 10000
		Axis 2 :
			Min_value is 0
			Max_value is 1023
			Resolution is 10000
		Axis 3 :
			Min_value is 0
			Max_value is 255
			Resolution is 10000
	(Axis 4-16 same as Axis-3)

michael@mc-desktop:~$ lshal | less
	...
	udi = '/org/freedesktop/Hal/devices/usb_device_172f_31_noserial'
	  info.linux.driver = 'usb'  (string)
	  info.parent = '/org/freedesktop/Hal/devices/usb_device_5e3_608_noserial'  (string)
	  info.product = 'Slim Tablet'  (string)
	  info.subsystem = 'usb_device'  (string)
	  info.udi = '/org/freedesktop/Hal/devices/usb_device_172f_31_noserial'  (string)
	  info.vendor = 'WALTOP International Corp.'  (string)
	  linux.device_file = '/dev/bus/usb/001/011'  (string)
	  linux.hotplug_type = 2  (0x2)  (int)
	  linux.subsystem = 'usb'  (string)
	  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4.3'  (string)
	  usb_device.bus_number = 1  (0x1)  (int)
	  usb_device.can_wake_up = true  (bool)
	  usb_device.configuration_value = 1  (0x1)  (int)
	  usb_device.device_class = 0  (0x0)  (int)
	  usb_device.device_protocol = 0  (0x0)  (int)
	  usb_device.device_revision_bcd = 258  (0x102)  (int)
	  usb_device.device_subclass = 0  (0x0)  (int)
	  usb_device.is_self_powered = false  (bool)
	  usb_device.linux.device_number = 11  (0xb)  (int)
	  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4.3'  (string)
	  usb_device.max_power = 100  (0x64)  (int)
	  usb_device.num_configurations = 1  (0x1)  (int)
	  usb_device.num_interfaces = 1  (0x1)  (int)
	  usb_device.num_ports = 0  (0x0)  (int)
	  usb_device.product = 'Slim Tablet'  (string)
	  usb_device.product_id = 49  (0x31)  (int)
	  usb_device.speed = 12.0 (12) (double)
	  usb_device.vendor = 'WALTOP International Corp.'  (string)
	  usb_device.vendor_id = 5935  (0x172f)  (int)
	  usb_device.version = 1.1 (1.1) (double)

	udi = '/org/freedesktop/Hal/devices/usb_device_172f_31_noserial_if0'
	  info.linux.driver = 'usbhid'  (string)
	  info.parent = '/org/freedesktop/Hal/devices/usb_device_172f_31_noserial'  (string)
	  info.product = 'USB HID Interface'  (string)
	  info.subsystem = 'usb'  (string)
	  info.udi = '/org/freedesktop/Hal/devices/usb_device_172f_31_noserial_if0'  (string)
	  linux.hotplug_type = 2  (0x2)  (int)
	  linux.subsystem = 'usb'  (string)
	  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4.3/1-4.3:1.0'  (string)
	  usb.bus_number = 1  (0x1)  (int)
	  usb.can_wake_up = true  (bool)
	  usb.configuration_value = 1  (0x1)  (int)
	  usb.device_class = 0  (0x0)  (int)
	  usb.device_protocol = 0  (0x0)  (int)
	  usb.device_revision_bcd = 258  (0x102)  (int)
	  usb.device_subclass = 0  (0x0)  (int)
	  usb.interface.class = 3  (0x3)  (int)
	  usb.interface.number = 0  (0x0)  (int)
	  usb.interface.protocol = 0  (0x0)  (int)
	  usb.interface.subclass = 0  (0x0)  (int)
	  usb.is_self_powered = false  (bool)
	  usb.linux.device_number = 11  (0xb)  (int)
	  usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4.3/1-4.3:1.0'  (string)
	  usb.max_power = 100  (0x64)  (int)
	  usb.num_configurations = 1  (0x1)  (int)
	  usb.num_interfaces = 1  (0x1)  (int)
	  usb.num_ports = 0  (0x0)  (int)
	  usb.product = 'USB HID Interface'  (string)
	  usb.product_id = 49  (0x31)  (int)
	  usb.speed = 12.0 (12) (double)
	  usb.vendor = 'WALTOP International Corp.'  (string)
	  usb.vendor_id = 5935  (0x172f)  (int)
	  usb.version = 1.1 (1.1) (double)

	udi = '/org/freedesktop/Hal/devices/usb_device_172f_31_noserial_if0_logicaldev_input'
	  info.capabilities = {'input', 'input.mouse', 'input.tablet'} (string list)
	  info.category = 'input'  (string)
	  info.parent = '/org/freedesktop/Hal/devices/usb_device_172f_31_noserial_if0'  (string)
	  info.product = 'WALTOP International Corp. Slim Tablet'  (string)
	  info.subsystem = 'input'  (string)
	  info.udi = '/org/freedesktop/Hal/devices/usb_device_172f_31_noserial_if0_logicaldev_input'  (string)
	  input.device = '/dev/input/event8'  (string)
	  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_172f_31_noserial_if0'  (string)
	  input.product = 'WALTOP International Corp. Slim Tablet'  (string)
	  input.x11_driver = 'evdev'  (string)
	  linux.device_file = '/dev/input/event8'  (string)
	  linux.hotplug_type = 2  (0x2)  (int)
	  linux.subsystem = 'input'  (string)
	  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4.3/1-4.3:1.0/input/input28/event8'  (string)
	...

Alternate WACOM Driver workarounds (functionality removed 8/09)
	[https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)
	[http://ubuntuforums.org/showpost.php?p=8684100&postcount=124](http://ubuntuforums.org/showpost.php?p=8684100&postcount=124)
	[http://wiki.archlinux.org/index.php/Wacom_Tablet](http://wiki.archlinux.org/index.php/Wacom_Tablet)

---

### Post by emaydubya on 2010-01-27
I think it's supposed to work with the wacom drivers and it can but without pressure.
I've been over hundreds of posts and can't get it to work at all anymore. I think i've stuffed my install completely by trying too many "fixes" and am waiting for 10.04 to do a fresh install and try again. Probably two months to go.

Yep, it used to work out of the box with 8.04 or 8.10, can't remember but the working function was removed and my tablet became useless.

Waltop themselves released a driver not too long ago but I can't get that to compile either.

---

### Post by emaydubya on 2010-02-13
I got it working..
See here: [http://ubuntuforums.org/showpost.php?p=8802271&postcount=23](http://ubuntuforums.org/showpost.php?p=8802271&postcount=23)

---

