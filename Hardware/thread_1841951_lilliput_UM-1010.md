---
title: "lilliput UM-1010"
date: 2011-09-10
forum: Hardware
---

### Post by spamalam on 2011-09-10
[http://www.lilliputweb.net/index.php?Controller=User_Product&action=ShowProduct&product_id=105](http://www.lilliputweb.net/index.php?Controller=User_Product&action=ShowProduct&product_id=105)

I have one of these devices and it works in windows without issues.  Ubuntu 11.04 however is just displaying a green screen.  The touch appears to work but is inversed and spread across my two other desktops (ie. I touch the left of the screen and it 'clicks' the far right of my right monitor, i touch the right and it 'clicks the far left of my main monitor).

Can anyone help me get this device working under 11.04 of ubuntu?

The monitor is a displaylink device, powered by usb.  When I plug it in:
```

dmsg
[  878.000270] usb 1-1.1: new high speed USB device using ehci_hcd and address 12
[  878.110631] hub 1-1.1:1.0: USB hub found
[  878.110800] hub 1-1.1:1.0: 4 ports detected
[  878.389192] usb 1-1.1.1: new full speed USB device using ehci_hcd and address 13
[  878.503972] input: eGalax Inc. USB TouchController as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1.1/1-1.1.1:1.0/input/input12
[  878.504305] input: eGalax Inc. USB TouchController as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1.1/1-1.1.1:1.0/input/input13
[  878.504520] generic-usb 0003:0EEF:0001.0004: input,hidraw0: USB HID v2.10 Pointer [eGalax Inc. USB TouchController] on usb-0000:00:1a.0-1.1.1/input0
[  878.598494] usb 1-1.1.2: new high speed USB device using ehci_hcd and address 14
[  878.723759] udlfb: DisplayLink LILLIPUT USB Monitor - serial #89152961
[  878.723768] udlfb: vid_17e9&pid_02a9&rev_0127 driver's dlfb_data struct at ffff8801af893800
[  878.723773] udlfb: console enable=0
[  878.723777] udlfb: fb_defio enable=0
[  878.724010] udlfb: vendor descriptor length:17 data:17 5f 01 0015 05 00 01 03 00 04
[  878.724015] udlfb: DL chip limited to 700000 pixel modes
[  878.724079] udlfb: allocated 4 65024 byte urbs
[  878.822523] udlfb: 1024x600 valid mode
[  878.822530] udlfb: Reallocating framebuffer. Addresses will change!
[  878.824527] udlfb: 1024x600 valid mode
[  878.824531] udlfb: set_par mode 1024x600
[  878.827746] udlfb: DisplayLink USB device /dev/fb1 attached. 1024x600 resolution. Using 2400K framebuffer memory

```

---

### Post by dclapp on 2011-09-14
I was able to get it going except for the right click capabilty (by holding down the pointer on the screen).

You need the following packages
xserver-xorg-input-evdev
xinput
xinput-calibrator

The next trick is you need to blacklist the usbtouchscreen driver.

Add the following line to /etc/modprobe.d/blacklist.conf

#disable usb touch driver
blacklist usbtouch

Then re-start system and see if you can run the the xinput-calibrator program.

You will need to add the calibration file to xorg.conf file as the program suggests to have it come up correctly each time (99-calibration.conf, I believe).

I have been trying to upate to the latest version of xf86-inputs-evdev which has right click emulation, but have not been able to make it work...

Hope it helps

cheers,

dc

---

### Post by dugald on 2012-07-19
I have tried to get this screen working in 10.04 and 12.04 with no success. Haven't statred on getting the touch input to work as I can't even get the screen to display anything (just a green screen).  I get pretty much the same from dmesg as in the first post and the steps in the second post don't help at all.  

I have the displaylink driver installed and I am on kernel 3.2.  Anyone had any luck getting this to work?

Dugald

---

