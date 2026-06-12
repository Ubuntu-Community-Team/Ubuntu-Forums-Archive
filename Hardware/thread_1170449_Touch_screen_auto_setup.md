---
title: "Touch screen auto setup?"
date: 2009-05-26
forum: Hardware
---

### Post by acidd_uk on 2009-05-26
I'm trying to get a Panasonic CF-19 Mk3 working with Jaunty. I've got pretty much everything working now, with the exception of the touch screen.

It is detected by udev and assigned a /dev/input/eventX node, and it is actually functional in X without any manual intervention needed, but the calibration is out. Looking at the existing forum posts on the subject of touch screens, it seems that in the past, specific drivers were needed to let Xorg use the device. However, I guess this is no longer necessary.

My (auto generated) /etc/X11/xorg.conf is pretty skeletal, with only a video device, monitor and screen defined. The touchpad, touch screen, keyboard, vga adapter etc are all autodetected by Xorg. I don't know anything about this auto-detection process.

So, in the past, the touchscreen calibration was done via "Option" elements in the "InputDevice" section of xorg.conf.

So, is it possibly to calibrate the touchsceen while still letting xorg autodetect its presence? If not, then presumably I need to add a section to xorg.conf for the touchscreen. If this is the case, then what driver do I use?

Here's some system info...

Fragment of /proc/bus/input/devices:
```
I: Bus=0003 Vendor=0430 Product=0501 Version=0100
N: Name="Fujitsu Component USB Touch Panel"
P: Phys=usb-0000:00:1a.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/input/input5
U: Uniq=
H: Handlers=mouse1 event5 js0
B: EV=1b
B: KEY=70000 0 0 0 0 0 0 0 0
B: ABS=3
B: MSC=10
```

Fragments of /var/log/udev:
```
KERNEL[1243377010.487174] add      /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/0003:0430:0501.0001 (hid)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/0003:0430:0501.0001
SUBSYSTEM=hid
HID_ID=0003:00000430:00000501
HID_NAME=Fujitsu Component USB Touch Panel
HID_PHYS=usb-0000:00:1a.0-2/input0
DRIVER=generic-usb
MODALIAS=hid:b0003v00000430p00000501
SEQNUM=1613
```
```
KERNEL[1243377010.501199] add      /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/input/input5 (input)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/input/input5
SUBSYSTEM=input
PRODUCT=3/430/501/100
NAME="Fujitsu Component USB Touch Panel"
PHYS="usb-0000:00:1a.0-2/input0"
UNIQ=""
EV==1b
KEY==70000 0 0 0 0 0 0 0 0
ABS==3
MSC==10
MODALIAS=input:b0003v0430p0501e0100-e0,1,3,4,k110,111,112,ra0,1,m4,lsfw
SEQNUM=1614
```
```
KERNEL[1243377011.501199] add      /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/0003:0430:0501.0001 (hid)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/0003:0430.0501
SUBSYSTEM=hid
HID_ID=0003:00000430:00000501
HID_NAME=Fujitsu Component USB Touch Panel
HID_PHYS=usb-0000:00:1a.0-2/input0
DRIVER=generic-usb
MODALIAS=hid:b0003v00000430p00000501
SEQNUM=1613
```
```
KERNEL[1243377011.282420] add      /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/input/input5 (input)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/input/input5
SUBSYSTEM=input
PRODUCT=3/430/501/100
NAME="Fujitsu Component USB Touch Panel"
PHYS="usb-0000:00:1a.0-2/input0"
UNIQ=""
EV==1b
KEY==70000 0 0 0 0 0 0 0 0
ABS==3
MSC==10
MODALIAS=input:b0003v0430p0501e0100-e0,1,3,4,k110,111,112,ra0,1,m4,lsfw
SEQNUM=1614
```
```
UDEV  [1243377011.296177] add       /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/input/input5/js0 (input)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/input/input5/js0
SUBSYSTEM=input
SEQNUM=1669
ID_VENDOR=Fujitsu_Component
ID_VENDOR_ENC=Fujitsu\x20Component
ID_VENDOR_ID=0430
ID_MODEL=USB_Touch_Panel
ID_MODEL_ENC=USB\x20Touch\x20Panel
ID_MODEL_ID=0501
ID_REVISION=1002
ID_SERIAL=Fujitsu_Component_USB_Touch_Panel
ID_TYPE=hid
ID_BUS=usb
ID_USB_INTERFACES=:030102:
ID_USB_INTERFACE_NUM=00
ID_USB_DRIVER=usbhid
ID_CLASS=joystick
ID_PATH=pci-0000:00:1a.0-usb-0:2:1.0
DEVNAME=/dev/input/js0
MAJOR=13
MINOR=0
DEVLINKS=/dev/char/13:0 /dev/input/by-id/usb-Fujitsu_Component_USB_Touch_Panel-joystick /dev/input/by-path/pci-0000:00:1a.0-usb-0:2:1.0-joystick

UDEV  [1243377011.300265] add       /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/input/input5/mouse1 (input)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/input/input5/mouse1
SUBSYSTEM=input
SEQNUM=1617
ID_VENDOR=Fujitsu_Component
ID_VENDOR_ENC=Fujitsu\x20Component
ID_VENDOR_ID=0430
ID_MODEL=USB_Touch_Panel
ID_MODEL_ENC=USB\x20Touch\x20Panel
ID_MODEL_ID=0501
ID_REVISION=1002
ID_SERIAL=Fujitsu_Component_USB_Touch_Panel
ID_TYPE=hid
ID_BUS=usb
ID_USB_INTERFACES=:030102:
ID_USB_INTERFACE_NUM=00
ID_USB_DRIVER=usbhid
ID_CLASS=joystick
ID_PATH=pci-0000:00:1a.0-usb-0:2:1.0
DEVNAME=/dev/input/mouse1
MAJOR=13
MINOR=33
DEVLINKS=/dev/char/13:33 /dev/input/by-id/usb-Fujitsu_Component_USB_Touch_Panel-joystick /dev/input/by-path/pci-0000:00:1a.0-usb-0:2:1.0-joystick

UDEV  [1243377011.302026] add       /devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/input/input5/event5 (input)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1a.0/usb3/3-2/3-2:1.0/input/input5/event5
SUBSYSTEM=input
SEQNUM=1620
ID_VENDOR=Fujitsu_Component
ID_VENDOR_ENC=Fujitsu\x20Component
ID_VENDOR_ID=0430
ID_MODEL=USB_Touch_Panel
ID_MODEL_ENC=USB\x20Touch\x20Panel
ID_MODEL_ID=0501
ID_REVISION=1002
ID_SERIAL=Fujitsu_Component_USB_Touch_Panel
ID_TYPE=hid
ID_BUS=usb
ID_USB_INTERFACES=:030102:
ID_USB_INTERFACE_NUM=00
ID_USB_DRIVER=usbhid
ID_CLASS=joystick
ID_PATH=pci-0000:00:1a.0-usb-0:2:1.0
DEVNAME=/dev/input/event5
MAJOR=13
MINOR=69
DEVLINKS=/dev/char/13:69 /dev/input/by-id/usb-Fujitsu_Component_USB_Touch_Panel-event-joystick /dev/input/by-path/pci-0000:00:1a.0-usb-0:2:1.0-event-joystick
```

Edit: Also see general Toughbook CF-19 Mk3 thread:
[http://ubuntuforums.org/showthread.php?p=7348742](http://ubuntuforums.org/showthread.php?p=7348742)

---

### Post by emacspy on 2009-05-27
I am having the same headache as you on the mk3 acidd using linuxwacom I cannot run the calibration app. I will try to work on this but let me know likewise if anything turns up thanks.

---

### Post by jboning on 2009-05-28
I am having similar problems on a CF-30 (with the same Fujitsu Component USB Touch Panel). I'm actually poking at it on Slackware right now (though I might end up switching it back to Ubuntu).

The default xorg.conf has one pointer input device /dev/mouse -> /dev/input/mice, which gets input from both the touchscreen (/dev/input/mouse1) and the touchpad (/dev/input/mouse2); it's treating the touchscreen as a mouse. It looks like X needs a proper input driver for the touchscreen, but I haven't been able to find one. (Though using the joystick driver on /dev/input/js0 was slightly amusing).

I don't know much about X input modules, but if I can't find a way to make this work, I'm considering diving in and getting my hands dirty hacking something up.

---

### Post by acidd_uk on 2009-05-28
I actually ended up solving the problem by using the touchscreen driver for the CF-19 Mk2 that we had at work. I'm not sure on the staus of this driver, but I'll try to remember to check and if it's non-proprietry ill post the source up here. Unfortunately, this means you have to resort back to manually hacking xorg.conf to add it as an input device, and add the calibration parameters as options to the driver.

I would much rather know how Xorg is autodetecting it and where the configuration for it is - for example, what calibration parameters does the autodetected device use? As jboning said, I think getting any further would involve loowing at the raw output of the touchscreen from /dev/input/eventX and how the touchscreen driver I have processes that and how that then feeds into Xorg.

---

### Post by rabbitofdeath on 2009-12-14
Has there been any update on this? I have a MK3 CF-19 as well and can't seem to get any touchscreen functions to work properly.

---

### Post by csnow on 2009-12-30
So do I.
I have already tried the Ubuntu v9.10. It seems have touch function but it cannot touch on the correct position. 
I found that the OS had missed the "c:/etc/X11/xorg.conf". 
 
Any experts find the solution??

---

### Post by acidd_uk on 2010-09-03
I have since left the workplace where I was trying to sort this out, so I have not made any progress on this for approx a year! However, I have an IM from jeebustrain that might be useful to someone else, regarding touchscreen calibration:

> 
Hi. Actually it was there when I installed it. I remember having to search for it on 8.10 but I went through synaptic to try and find it on 9.04 I couldn't locate it. The exact name of the executable is "gksu /usr/bin/calibrate_touchscreen"

see if you can find that. It's in the Administration menu for me. Check to make sure you have the second one - it might be part of that package.

According to synaptic, the only touchscreen items I have installed are:
xserver-xorg-input-evtouch
libts-0.0-0


Sorry about the delayed reply. Let me know if there's something else I can do. I've gone through like 10 different distros on this CF-74 and other than some occasional screen brightness quirkyness, Jaunty has been absolutely flawless.


---

### Post by jeebustrain on 2010-09-27
did anyone's Toughbook touchscreen go to crap on Lucid? I did a fresh install on my CF-74 and nope - nada. Touchscreen is gone. Unfortunately, I don't have any of my Jaunty config files left (I guess I could reinstall and reconfigure to try and grab them if I run out of things to try).


I've been playing with some of the ideas in [this](http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/panasonic-toughbook-cf-29-touch-screen-485053/page14.html) thread. This is the device output of my touchscreen:

$ cat /proc/bus/input/devices
```

I: Bus=0003 Vendor=0430 Product=0501 Version=0100
N: Name="Fujitsu Takamisawa USB Touch Panel"
P: Phys=usb-0000:00:1d.1-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input7
U: Uniq=
H: Handlers=mouse1 event7 js0 
B: EV=1b
B: KEY=70000 0 0 0 0 0 0 0 0
B: ABS=3
B: MSC=10

```

I created a conf file snippet at /usr/lib/X11/xorg.conf.d/90-touchscreen.conf
```

Section "InputDevice"
        Identifier      "Fujitsu Takamisawa USB Touch Panel"
        Driver          "evtouch"
        Option          "Device" "/dev/input/event7"
        Option          "DeviceName" "touchscreen"
        Option          "MinX" "235"
        Option          "MinY" "305"
        Option          "MaxX" "4000"
        Option          "MaxY" "3830"
        Option          "MoveLimit" "5"
        Option          "ReportingMode" "Raw"
        Option          "SendCoreEvents" "true"
        Option          "Emulate3Buttons" "true"
        Option          "Emulate3Timeout" "40"
        Option          "AutoServerLayout" "on"
        Option          "AccelerationProfile" "-1"
EndSection

```

I have both xserver-xorg-input-evtouch and xserver-xorg-input-evdev installed.

Part of me thinks I just have the wrong "Device" option in my conf file, but then again, I might be on the completely wrong path. Does anyone have their Toughbook CF-74 touchscreen working properly?

I'm not sure

---

### Post by jeebustrain on 2010-09-28
well - I figured out my problem (at least I'm pretty sure). I think my touchscreen is just dead. It was acting up a few months back before I upgraded it and I just attributed it to something screwy in my xorg config. I just loaded up a Karmic live CD and installed xserver-xorg-input-evtouch and tried to run the calibration tool and it doesn't even pick up any input. 

I did some reading in the Toughbook forum on notebookreview.com and apparently the touchscreen just dying is not an uncommon occurance. 

Well fiddlesticks... At least the rest of the laptop works. Not bad for being almost 4.5 years old.

---

