---
title: "Aiptek type graphics tablet: how to set up with 14.04 LTS?"
date: 2014-11-22
forum: Hardware
---

### Post by Keith_Beef on 2014-11-22
So I have this graphics tablet that I bought a couple of years ago, second hand. It looks very much like the Trust model shown below, right down to the little indentations on the mouse buttons.

[IMG]http://www.wurwaldesign.com/blog/wp-content/uploads/2010/03/trust400.jpg[/IMG]

I want to get this working so that I can experiment with recognizing simplified Chinese and Kanji&#8230;

I had this working with an older version of Ubuntu, on a second computer, but I can't for the life of me remember what I did. It can't have been very difficult or complicated, because I have no recollection other than finding it easy to set up. 

But now, I'm having trouble figuring out what to do and also finding information about it.

Here's what I've done so far.

Inspired by [this page]("https://help.ubuntu.com/community/AiptekTablet"), I created /usr/share/X11/xorg.conf.d/50-aiptek.conf

```
Section "InputClass"
        Identifier "Aiptek class"
        MatchProduct "Aiptek|AIPTEK|aiptek"
        MatchDevicePath "/dev/input/event*"
        Driver "aiptek"
        Option "USB" "on"
        Option "Type" "stylus"
        Option "Mode" "absolute"
        Option "zMin" "0"
        Option "zMax" "511"
EndSection
```

Rebooted with the tablet plugged in.

The tablet is detected:
```
$ dmesg | grep -i aiptek
[    2.466379] usb 8-2: Manufacturer: AIPTEK International Inc.
[   27.795375] aiptek 8-2:1.0: Aiptek using 400 ms programming speed
[   27.795433] input: Aiptek as /devices/pci0000:00/0000:00:1d.1/usb8/8-2/8-2:1.0/input/input8
[   27.795599] usbcore: registered new interface driver aiptek

```
The module is loaded:
```
$ lsmod | grep -i aiptek
aiptek                 24487  0 
```

Unplugged the tablet from the computer, plugged it into the USB hub.
```
$ dmesg | tail -n 8
[ 1274.620067] usb 8-2: USB disconnect, device number 2
[ 1313.228264] usb 1-2.3: new low-speed USB device number 7 using ehci-pci
[ 1313.327011] usb 1-2.3: New USB device found, idVendor=08ca, idProduct=0010
[ 1313.327014] usb 1-2.3: New USB device strings: Mfr=1, Product=3, SerialNumber=0
[ 1313.327017] usb 1-2.3: Product: USB Tablet Series Version 1.05
[ 1313.327020] usb 1-2.3: Manufacturer: AIPTEK International Inc.
[ 1315.753637] aiptek 1-2.3:1.0: Aiptek using 400 ms programming speed
[ 1315.753736] input: Aiptek as /devices/pci0000:00/0000:00:1a.7/usb1/1-2/1-2.3/1-2.3:1.0/input/input20
```

```
$ lsusb | grep -i aiptek
Bus 001 Device 007: ID 08ca:0010 Aiptek International, Inc. Tablet
```

The tablet doesn't show up as an input device in Gimp's preferences. Inkscape lists a "Pressure sensitive tablet", but I don't see any effect from activating or disactivating this. 

So after looking around a bit more, I think that just having the aiptek driver loaded is not enough, I also need xserver-xorg-input-aiptek. But when I try to install that, Synaptic complains:

```
xserver-xorg-input-aiptek:
 Depends: xorg-input-abi-16
```

But synaptic cannot find xorg-input-abi-16.


Any ideas?

---

