---
title: "Weird USB device: &quot;05ac:0301 Apple, Inc. USB Mouse [Mitsumi, M4848]&quot;"
date: 2013-04-05
forum: Hardware
---

### Post by sanderj on 2013-04-05
I have a no-noname USB-stick that should pop-up a commercial website. I expected it to be a USB-flash-drive, with some Windows-auto-start, but under Ubuntu I don't see a drive at all.

So ... what kind of device is this?

lsusb says:

```
Bus 001 Device 008: ID 05ac:0301 Apple, Inc. USB Mouse [Mitsumi, M4848]
```

Apple? I don't think so (see the picture below).

When inserting, dmesg says:

```
[23667.799706] usb 1-1.2: new full-speed USB device number 9 using ehci-pci
[23667.893713] usb 1-1.2: New USB device found, idVendor=05ac, idProduct=0301
[23667.893723] usb 1-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=2
[23667.893728] usb 1-1.2: Product: WEBKEY
[23667.893733] usb 1-1.2: Manufacturer: FET-M-0101
[23667.893737] usb 1-1.2: SerialNumber: WEBKEY
[23667.895908] input: FET-M-0101 WEBKEY as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input19
[23667.896289] hid-generic 0003:05AC:0301.0009: input,hidraw1: USB HID v1.10 Keyboard [FET-M-0101 WEBKEY] on usb-0000:00:1a.0-1.2/input0

```

It's a keyboard? If so, would it - under Windows - type in some letters ("Windows-key", E, "www.blablaba.com"<ENTER") to open the meant URL?

Anyway: tips on what this is?

Running Ubuntu 13.04 daily update

[IMG]http://d3j5vwomefv46c.cloudfront.net/photos/large/754473175.jpg[/IMG]

---

### Post by cbanakis on 2013-04-05
Maybe a dongle for a wireless keyboard/mouse?

Looks like something that could snap into the bottom of a mouse for safe keeping.

---

### Post by sanderj on 2013-04-05
I just found this page: [http://www.dainile.lt/?p=540](http://www.dainile.lt/?p=540) Via Google Translate I was able to understand it: that device (similar / same to mine) seems to be a dedicated device to open a URL (under Windows), where the URL is in an EEPROM

"And now about the operation - when connected to a USB key Windows'am it presents itself as a HID device with a keyboard function (Amendment  ), which runs the Run (Win + R), and as I told you record the page address and numyga ENTER"

So in that way it indeed acts as a keyboard ... :-)

Strangely enough, nothing happens in my terminal when I plug the device in.
And I can't find a device /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input19 ...

EDIT: The commerical name seems to be "USB Webkey", used for promotional / marketing activities. ... Ah, there is even such an URL [http://www.webkey.com/](http://www.webkey.com/) (warning: that's a commercial site)

---

