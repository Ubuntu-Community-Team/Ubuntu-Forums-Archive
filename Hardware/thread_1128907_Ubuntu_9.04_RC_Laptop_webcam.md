---
title: "Ubuntu 9.04 RC Laptop webcam"
date: 2009-04-18
forum: Hardware
---

### Post by lavinia on 2009-04-18
Hello all.
i download ubuntu 9.04 after installed to my laptop. Perfect OS. i love you linux-ubuntu. 
This version of Ubuntu Linux is my laptop all drivers recognized.

i have a problem. It seems the reverse image of my webcam.

Details:
lavinya@lavinya-laptop:~$ lsusb
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 002: ID 0402:5602 ALi Corp. Video Camera Controller
....

	
How to fix?

---

### Post by lavinia on 2009-04-18
Detailed results:

hwinfo:
```
07: USB 00.0: 0000 Unclassified device
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_402_5602_noserial_if0
  Unique ID: 2UT6.qSFQ6Cc6sG8
  Parent ID: k4bc.cO89g+iefn1
  SysFS ID: /devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:1.0
  SysFS BusID: 1-3:1.0
  Hardware Class: unknown
  Model: "ALi USB2.0 Camera"
  Hotplug: USB
  Vendor: usb 0x0402 "ALi Corp."
  Device: usb 0x5602 "USB2.0 Camera"
  Revision: "1.00"
  Driver: "ALi m5602"
  Driver Modules: "gspca_m5602"
  Speed: 480 Mbps
  Module Alias: "usb:v0402p5602d0100dc00dsc00dp00icFFiscFFipFF"
  Driver Info #0:
    Driver Status: gspca_m5602 is active
    Driver Activation Cmd: "modprobe gspca_m5602"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #14 (Hub)
```

lsusb result: 
```
Bus 001 Device 002: ID 0402:5602 ALi Corp. Video Camera Controller
```

MORE:
```
Video Camera Controller
Property	Value
info.subsystem	usb_device
info.product	Video Camera Controller
info.vendor	ALi Corp.
info.parent	/org/freedesktop/Hal/devices/usb_device_1d6b_2_0000_00_1a_7
info.linux.driver	usb
info.udi	/org/freedesktop/Hal/devices/usb_device_402_5602_noserial
usb_device.linux.sysfs_path	/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-3
usb_device.linux.device_number	2
usb_device.is_self_powered	False
usb_device.vendor_id	1026
usb_device.vendor	ALi Corp.
usb_device.product_id	22018
usb_device.device_protocol	0
usb_device.device_revision_bcd	256
usb_device.device_subclass	0
usb_device.speed	480.0
usb_device.configuration_value	1
usb_device.bus_number	1
usb_device.product	Video Camera Controller
usb_device.num_configurations	1
usb_device.version	2.0
usb_device.num_ports	0
usb_device.max_power	500
usb_device.device_class	0
usb_device.can_wake_up	True
usb_device.num_interfaces	1
linux.device_file	/dev/bus/usb/001/002
linux.hotplug_type	2
linux.subsystem	usb
linux.sysfs_path	/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-3 


USB2.0 Camera
Property	Value
info.category	video4linux
info.subsystem	video4linux
info.product	USB2.0 Camera
info.parent	/org/freedesktop/Hal/devices/usb_device_402_5602_noserial
info.capabilities	video4linux video4linux.video_capture access_control
info.udi	/org/freedesktop/Hal/devices/usb_device_402_5602_noserial_video4linux
info.callouts.add	hal-acl-tool --add-device
info.callouts.remove	hal-acl-tool --remove-device
video4linux.device	/dev/video0
video4linux.version	2
access_control.type	video4linux
access_control.file	/dev/video0
linux.device_file	/dev/video0
linux.hotplug_type	2
linux.subsystem	video4linux
linux.sysfs_path	/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-3/video4linux/video0


USB Vendor Specific Interface
Property	Value
info.subsystem	usb
info.product	USB Vendor Specific Interface
info.udi	/org/freedesktop/Hal/devices/usb_device_402_5602_noserial_if0
info.parent	/org/freedesktop/Hal/devices/usb_device_402_5602_noserial
info.linux.driver	ALi m5602
usb.linux.sysfs_path	/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:1.0
usb.linux.device_number	2
usb.is_self_powered	False
usb.vendor_id	1026
usb.vendor	ALi Corp.
usb.product_id	22018
usb.device_protocol	0
usb.device_revision_bcd	256
usb.device_subclass	0
usb.speed	480.0
usb.configuration_value	1
usb.bus_number	1
usb.product	USB Vendor Specific Interface
usb.num_configurations	1
usb.version	2.0
usb.num_ports	0
usb.max_power	500
usb.device_class	0
usb.interface.protocol	255
usb.interface.class	255
usb.interface.subclass	255
usb.interface.number	0
usb.can_wake_up	True
usb.num_interfaces	1
linux.hotplug_type	2
linux.subsystem	usb
linux.sysfs_path	/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-3/1-3:1.0 

```

	
Please help me.

---

### Post by falstaff on 2009-04-18
Do i understand that correctly, the image of your webcam is upside down? Or is it just flipped vertically?

Did it worked with earlier versions of ubuntu?

---

### Post by lavinia on 2009-04-18
> **falstaff said:**
> Do i understand that correctly, the image of your webcam is upside down? Or is it just flipped vertically?

Did it worked with earlier versions of ubuntu?

Thanks for reply falstaff. 
Sory my english not enought. yes my webcam upside down. inverse image, video.

no not worked earlier versions. Only this I recognized in this version only my laptop webcam.

---

### Post by lavinia on 2009-04-18
If you have that helps you to understand, i will be happy.

---

### Post by plysovej_kaktus on 2009-04-21
xawtv can set vertical or horizontal mirroring and much more

```
apt-get install xawtv*
```

---

### Post by lavinia on 2009-04-22
Thanks for reply. Thank you very much :):lolflag:

But how to using xawtv? or in console command?
Re thanks.

---

### Post by Sharaazad on 2009-05-06
Same cam here, same problem. Please help :(

---

### Post by dragonhunter on 2009-05-09
Hello all

I have exactly the same camera, but on my laptop it doesn't even work. When you open camorama (as an example) it gives me a message saying "Unable to capture image", but on its GUI it shown me a "picture" from my webcam imagem in black and white and upside down. When you hit ok it close itself.
I've also tried to check the cam status on skype, but there it only shows me a green screen.

Does anyone have any idea what can I possibly do to fix it?

---

### Post by dragonhunter on 2009-05-09
Hi guys I believe this can help you.

[http://m560x-driver.wiki.sourceforge.net/howto_install](http://m560x-driver.wiki.sourceforge.net/howto_install)

---

### Post by Sharaazad on 2009-05-11
following instructions in your link i did:

```
v4lctrl -s 9963797 -v 1

```

with this the image is flipped and it's ok (so i have to put this line to be execute at startup).

The only problem is that image is black and white -.-

If i type again the command but with "-v 0", it returns upside down but with colors (lol)

any idea?

---

### Post by bsb on 2009-06-07
> **Sharaazad said:**
> 

```
v4lctrl -s 9963797 -v 1

```

with this the image is flipped and it's ok (so i have to put this line to be execute at startup).

The only problem is that image is black and white


I get the upside-down or b&w choice with cheese and skype too.

Additionally, with vlc run as:
 LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so vlc v4l2://

The stream starts corrupted, I have to fiddle with v4l 
parameters in vlc or run the following:
 ./src/v4lctrl -s 9963793 -v 20483
(set the exposure to the default value) in order to correct it.

I'm glad I finally have video, nonetheless.  It's great to
have hardware I'd basically written off suddenly start working
after an upgrade (hardy-..->jaunty)

---

### Post by AaronJS on 2009-06-20
Hello, 

I am brand new to Ubuntu and Linux.  I have been reading and reading for awhile now and am totally lost.  I am trying to get my webcam working along with everyone else.  I read this [http://m560x-driver.wiki.sourceforge.net/howto_install](http://m560x-driver.wiki.sourceforge.net/howto_install) and these postings but am lost on exactly what to do. I admit I used windows for years and just download and use the install.exe in the programs. i know this does not work in Ubuntu.  Can someone take the time to hold my hand and walk me through this process. Thanks for the help - Aaron

---

### Post by Sharaazad on 2009-11-08
Completely solved on Ubuntu 9.10 Karmic Koala, it works perfect out of the box :D

---

### Post by dragonhunter on 2009-11-16
Well I've upgraded my system instead of doing a brand new installation and on my Karmic my camera doesn't work anymore. Had to try to install the drivers again.

---

### Post by glavkos on 2009-12-09
> **Sharaazad said:**
> following instructions in your link i did:

```
v4lctrl -s 9963797 -v 1

```with this the image is flipped and it's ok (so i have to put this line to be execute at startup).

The only problem is that image is black and white -.-

If i type again the command but with "-v 0", it returns upside down but with colors (lol)

any idea?

Sorry but that command do not work in karmic (Ubuntu 9.10). 
I follow that [http://radu.cotescu.com/2009/11/05/flipped-images-ubuntu-webcam/](http://radu.cotescu.com/2009/11/05/flipped-images-ubuntu-webcam/)
but i must confuse something in the part where he refers to :
~/bin/webcamWrapper.sh:  [COLOR=#666666]*#!/bin/bash*[/COLOR]
[COLOR=#007800]LD_PRELOAD[/COLOR]=[COLOR=#000000]**/**[/COLOR]usr[COLOR=#000000]**/**[/COLOR]lib[COLOR=#000000]**/**[/COLOR]libv4l[COLOR=#000000]**/**[/COLOR]v4l1compat.so $[COLOR=#000000]1[/COLOR]
[COLOR=#7A0874]**exit**[/COLOR] [COLOR=#000000]0

i do not know how to create such a file and in which directory. 
Can anyone of you help me please?
[/COLOR]

---

### Post by jwmp on 2010-09-19
I realize this thread is pretty dead, but I came across it while searching for a solution to my problems. So here is the solution I discovered...

<https://sourceforge.net/tracker/?func=detail&atid=915340&aid=3032266&group_id=185953>

:P

---

