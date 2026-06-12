---
title: "Touchscreen setup, can't find it in /dev"
date: 2009-08-19
forum: Hardware
---

### Post by vman81 on 2009-08-19
I've been trying to set up an old POS touchscreen on ubuntu, but I'm pretty confused by now. 

It's a 3M M170 Microtouch screen, with a USB touch panel. When I assign the USB unit to WindowsXP under Virtualbox it works flawlessly (after i calibrate it with the windows tool)

It looks like Ubuntu sees it "correctly" according to my dmesg output when i reconnect it:

```
[ 1016.704632] usb 7-1: USB disconnect, address 2
[ 1022.884082] usb 7-1: new full speed USB device using uhci_hcd and address 3
[ 1023.100574] usb 7-1: configuration #1 chosen from 1 choice
[ 1024.582777] input: 3M 3M USB Touchscreen - EX II as /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input14

```

My problem is that ALL guides i've tried to follow need me to refer to a device like /dev/ttyS0 for calibration etc, but I simply can't find it.

When I press the screen i notice that I get a right click wherever my mouse cursor is located, and if i drag my finger horizontally across the screen, my browser scrolls vertically, so obviously something needs to be switched around.

I've tried testing for output on every imaginable device the same way i'd test my usb mouse with "cat /dev/usb/hiddev0" and move the mouse around to see input, but I can't get any input.

lsusb gives me the following:

lsusb | grep Tou
Bus 007 Device 003: ID 0596:0001 MicroTouch Systems, Inc. Touchscreen


A fried mentioned that he once used a tool that would display where input would come from, if he for example clicked the screen on the program. I don't know if I can explain this well enough.

[B]Anyways, my main issue is that seeing as the computer responds to the input (but uncalibrated etc), shouldn't there be something under /dev that i could "cat" to see my touches as input? How can i find it?
[/B]

Btw the drivers from the manufacturer didn't seem to install properly when i tried, spitting out a few error messages that i didn't save, and I've read several posts online saying that the built in drivers were good enough etc, I'm not quite prepared to go down that way again.

btw lshal gives me the following:
```
udi = '/org/freedesktop/Hal/devices/usb_device_596_1_noserial'
  info.linux.driver = 'usb'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_1d6b_1_0000_00_1d_1'  (string)
  info.product = 'Touchscreen'  (string)
  info.subsystem = 'usb_device'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_596_1_noserial'  (string)
  info.vendor = 'MicroTouch Systems, Inc.'  (string)
  linux.device_file = '/dev/bus/usb/007/003'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'usb'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-1'  (string)
  usb_device.bus_number = 7  (0x7)  (int)
  usb_device.can_wake_up = true  (bool)
  usb_device.device_class = 0  (0x0)  (int)
  usb_device.device_protocol = 0  (0x0)  (int)
  usb_device.device_revision_bcd = 1040  (0x410)  (int)
  usb_device.device_subclass = 0  (0x0)  (int)
  usb_device.is_self_powered = true  (bool)
  usb_device.linux.device_number = 3  (0x3)  (int)
  usb_device.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-1'  (string)
  usb_device.max_power = 100  (0x64)  (int)
  usb_device.num_configurations = 1  (0x1)  (int)
  usb_device.num_ports = 0  (0x0)  (int)
  usb_device.product = 'Touchscreen'  (string)
  usb_device.product_id = 1  (0x1)  (int)
  usb_device.speed = 12.0 (12) (double)
  usb_device.vendor = 'MicroTouch Systems, Inc.'  (string)
  usb_device.vendor_id = 1430  (0x596)  (int)
  usb_device.version = 1.1 (1.1) (double)

```


Edit1:

Actually the error from the manufacturer's driver install is the same as in this thread: [http://ubuntuforums.org/showthread.php?t=1237342&highlight=microtouch](http://ubuntuforums.org/showthread.php?t=1237342&highlight=microtouch)

"'update etc/init.d/TWDrvSartup &#8211; missing LSB header &#8220;required-start&#8221; and &#8220;required-stop&#8221;'

but the calibration tools never seemed to work etc, I'd rather not go that way again if i can help it.

---

### Post by vman81 on 2009-08-20
I've solved my problems now, and I thought I'd share.

Mostly by following the following post:
[http://ubuntuforums.org/showthread.php?t=1020019&highlight=microtouch](http://ubuntuforums.org/showthread.php?t=1020019&highlight=microtouch)

However, i did change some things to correct the rotated axis, and needed some diffrent calibration values for my 3M M170 screen:

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
        <device>
                <match key="input.product" contains="Touchscreen">
                        <merge key="input.x11_driver" type="string">evtouch</merge>
                        <merge key="input.x11_options.MinX" type="string">14000</merge>
                        <merge key="input.x11_options.MaxX" type="string">2560</merge>
                        <merge key="input.x11_options.MinY" type="string">2380</merge>
                        <merge key="input.x11_options.MaxY" type="string">14050</merge>
                        <merge key="input.x11_options.Rotate" type="string">CCW</merge>
                </match>
        </device>
</deviceinfo>
```

If you are going to change the values, please be adviced that the X or Y axis are switched by the CCW rotation I added, so "MinY" actually corresponds to the LEFT side, and not the Y axis as expected.

Also, as noted in the other post, using the built in tool for calibration SCREWS UP ROYALLY, giving a calibration that i can't quite dechipher, but reconnecting the USB connection resets this to what is in the /etc/hal/fdi/policy/touchscreen.fdi file. So just remove this tool before you accidentally use it. The problem returns after every reboot, and I can't seem to get that configuration removed, so I need to reconnect USB for every boot.

I'll post an update if/when i solve this issue.

Edit1:

Deleting everything except the min/max values in /etc/evtouch/config solved the messed up calibration on startup, now I just need to figure out how to reduce jitter, because most times i press the screen the cursor moves around a few pixels, so mouse presses on buttons aren't registered particularly well, and my poor cursor looks stressed :)

---

### Post by c.monty on 2009-08-23
TFT Touchscreen with eGalax Touch driver + USB Mouse -> weired mouse pointer action

hi!

i'm running ubuntu 9.04, kernel 2.6.28-15-generic, X server X.Org X Server 1.6.0 Release Date: 2009-2-25 X Protocol Version 11, Revision 0.

to get the TFT touchscreen working, i've installed package xserver-xorg-input-evtouch and driver eGalax Touch driver for 32bit Linux kernel 2.6.x, version 2.06.2905-32b-k26.

output of cat /proc/bus/input/devices
```

I: Bus=0003 Vendor=0eef Product=0001 Version=0112
N: Name="eGalax Inc. Touch"
P: Phys=usb-0000:00:1d.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input5
U: Uniq=
H: Handlers=mouse1 event3
B: EV=1b
B: KEY=401 0 30000 0 0 0 0 0 0 0 0
B: ABS=f
B: MSC=10

```
everthing works fine UNTIL i plugin USB mouse controller.
then the mouse controller is not working properly, means the pointer is moving on the screen, but i cannot select anything.

this problem is described [here]("http://www.conan.de/touchscreen/evtouch.html urltitle")
"Since Xorg 7.2 there is always a default-mouse-pointer which will run simultaneously with evtouch if you do not prevent it from loading. It is extremely important that you add the following to your configuration. Otherwise you will get double click events and all kind of strange things."

but as HAL is used i don't know how this should be implemented.

can someone assist here?

THX

---

### Post by davedumas0 on 2009-10-24
i have the same problem but my touch monitor is a 3m m170 serial but my mobo does not have a serial i have a usb serial converter  im not sure how to get the touch to work please help




my system:
asus striker 2 extreme mobo
a qx9650 cpu
4 gig ddr3
gtx 260 
ubuntu 9.04 fully updated

---

### Post by davedumas0 on 2009-10-25
bump

---

### Post by davedumas0 on 2009-10-25
my pc can see the usb adapter but not the touch screen please help
it works fine in windows so i know it works

---

