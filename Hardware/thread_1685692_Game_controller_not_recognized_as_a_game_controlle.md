---
title: "Game controller not recognized as a game controller."
date: 2011-02-11
forum: Hardware
---

### Post by Nillerz on 2011-02-11
I am using a controller than identifies itself as a "Macally iShock II FFB Game Controller" in lshal. The layout is almost identical to a Playstation controller, and it is, as far as I can tell, fairly generic. It is not immediately recognized as a game controller by X.org, and is instead a generic USB device. 

If I hold the right analog stick down, and then move the left analog stick, I have rudimentary control of the mouse in a circle in the center of the screen. 

Using input-events from the input-utils package, I confirmed that the controller in question was outputting a steady data stream whenever either a button was pressed, or the analog stick was fiddled with. 

Here is my lsusb readout for this device:


Bus 002 Device 007: ID 2222:4020 MacAlly 


Here is the lshal portion regarding the device:

```
2c2
< Dumping 147 device(s) from the Global Device List:
---
> Dumping 150 device(s) from the Global Device List:
1367a1368,1448
> udi = '/org/freedesktop/Hal/devices/usb_device_2222_4020_noserial'
>   info.linux.driver = 'usb'  (string)
>   info.parent = '/org/freedesktop/Hal/devices/usb_device_424_2504_noserial'  (string)
>   info.product = 'Macally iShock II FFB Game Controller'  (string)
>   info.subsystem = 'usb_device'  (string)
>   info.udi = '/org/freedesktop/Hal/devices/usb_device_2222_4020_noserial'  (string)
>   info.vendor = 'MacAlly'  (string)
>   linux.device_file = '/dev/bus/usb/002/013'  (string)
>   linux.hotplug_type = 2  (0x2)  (int)
>   linux.subsystem = 'usb'  (string)
>   linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.2'  (string)
>   usb_device.bus_number = 2  (0x2)  (int)
>   usb_device.can_wake_up = false  (bool)
>   usb_device.configuration_value = 1  (0x1)  (int)
>   usb_device.device_class = 0  (0x0)  (int)
>   usb_device.device_protocol = 0  (0x0)  (int)
>   usb_device.device_revision_bcd = 256  (0x100)  (int)
>   usb_device.device_subclass = 0  (0x0)  (int)
>   usb_device.is_self_powered = false  (bool)
>   usb_device.linux.device_number = 13  (0xd)  (int)
>   usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.2'  (string)
>   usb_device.max_power = 100  (0x64)  (int)
>   usb_device.num_configurations = 1  (0x1)  (int)
>   usb_device.num_interfaces = 1  (0x1)  (int)
>   usb_device.num_ports = 0  (0x0)  (int)
>   usb_device.product = 'Macally iShock II FFB Game Controller'  (string)
>   usb_device.product_id = 16416  (0x4020)  (int)
>   usb_device.speed = 1.5 (1.5) (double)
>   usb_device.vendor = 'MacAlly'  (string)
>   usb_device.vendor_id = 8738  (0x2222)  (int)
>   usb_device.version = 1.0 (1) (double)
> 
> udi = '/org/freedesktop/Hal/devices/usb_device_2222_4020_noserial_if0'
>   info.linux.driver = 'usbhid'  (string)
>   info.parent = '/org/freedesktop/Hal/devices/usb_device_2222_4020_noserial'  (string)
>   info.product = 'USB HID Interface'  (string)
>   info.subsystem = 'usb'  (string)
>   info.udi = '/org/freedesktop/Hal/devices/usb_device_2222_4020_noserial_if0'  (string)
>   linux.hotplug_type = 2  (0x2)  (int)
>   linux.subsystem = 'usb'  (string)
>   linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.2/2-1.2:1.0'  (string)
>   usb.bus_number = 2  (0x2)  (int)
>   usb.can_wake_up = false  (bool)
>   usb.configuration_value = 1  (0x1)  (int)
>   usb.device_class = 0  (0x0)  (int)
>   usb.device_protocol = 0  (0x0)  (int)
>   usb.device_revision_bcd = 256  (0x100)  (int)
>   usb.device_subclass = 0  (0x0)  (int)
>   usb.interface.class = 3  (0x3)  (int)
>   usb.interface.number = 0  (0x0)  (int)
>   usb.interface.protocol = 0  (0x0)  (int)
>   usb.interface.subclass = 0  (0x0)  (int)
>   usb.is_self_powered = false  (bool)
>   usb.linux.device_number = 13  (0xd)  (int)
>   usb.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.2/2-1.2:1.0'  (string)
>   usb.max_power = 100  (0x64)  (int)
>   usb.num_configurations = 1  (0x1)  (int)
>   usb.num_interfaces = 1  (0x1)  (int)
>   usb.num_ports = 0  (0x0)  (int)
>   usb.product = 'USB HID Interface'  (string)
>   usb.product_id = 16416  (0x4020)  (int)
>   usb.speed = 1.5 (1.5) (double)
>   usb.vendor = 'MacAlly'  (string)
>   usb.vendor_id = 8738  (0x2222)  (int)
>   usb.version = 1.0 (1) (double)
> 
> udi = '/org/freedesktop/Hal/devices/usb_device_2222_4020_noserial_if0_logicaldev_input'
>   info.capabilities = {'input', 'input.tablet'} (string list)
>   info.category = 'input'  (string)
>   info.parent = '/org/freedesktop/Hal/devices/usb_device_2222_4020_noserial_if0'  (string)
>   info.product = 'Macally Peripherals  Macally iShock II FFB Game Controller'  (string)
>   info.subsystem = 'input'  (string)
>   info.udi = '/org/freedesktop/Hal/devices/usb_device_2222_4020_noserial_if0_logicaldev_input'  (string)
>   input.device = '/dev/input/event9'  (string)
>   input.originating_device = '/org/freedesktop/Hal/devices/usb_device_2222_4020_noserial_if0'  (string)
>   input.product = 'Macally Peripherals  Macally iShock II FFB Game Controller'  (string)
>   linux.device_file = '/dev/input/event9'  (string)
>   linux.hotplug_type = 2  (0x2)  (int)
>   linux.subsystem = 'input'  (string)
>   linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.2/2-1.2:1.0/input/input14/event9'  (string)
> 
3278c3359
< Dumped 147 device(s) from the Global Device List.
---
> Dumped 150 device(s) from the Global Device List.
```

If anyone could help me out a bit here, that would be great. 

Is it possible to edit xorg.conf to recognize the device as a joypad, and if so, set it as js0? If I did that would the standard jscalibrate program work for it, analog sticks et al?

Or would I need a separate driver to be built for it?

Thanks in advance for any help given.

---

### Post by Nillerz on 2011-02-11
Nobody?

---

### Post by Stoppelmonster on 2011-09-27
I am having an issue with the same controller. Macally iShock II. I found [this thread]("http://ubuntuforums.org/archive/index.php/t-1583045.html") I created a 50-joystick.conf that contained:

> 
Section "InputClass"
Identifier "joystick catchall"
MatchIsJoystick "on"
MatchDevicePath "/dev/bus/usb/004/001*"
Driver "joystick"
 Option "StartKeysEnabled" "False"
    Option "StartMouseEnabled" "False"

EndSection

The emulator I am using, ZSNES was able to recognize the device but I have limited control and the buttons had no function. I assume I need to add more commands in the .conf but IDK what. 



so far that is the best help I've seen regarding this issue.

---

