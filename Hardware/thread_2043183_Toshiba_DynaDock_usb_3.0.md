---
title: "Toshiba DynaDock usb 3.0"
date: 2012-08-16
forum: Hardware
---

### Post by pborges on 2012-08-16
hey guys, i could really use some help trying to get some monitor support with my new dock, ([http://www.toshibadirect.com/td/b2c/adet.to?poid=499638](http://www.toshibadirect.com/td/b2c/adet.to?poid=499638))

it looks like it has a displaylink card in it,
the USB and networking work fine out of the box,
i can live w.o audio
but i would REALLY love to have three monitors on my desktop without reverting to windows 

i know there are some guru's out there,
help a brother out!

```
pborges@UX31A:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 008: ID 2109:0811  
Bus 004 Device 012: ID 2109:0811  
Bus 001 Device 003: ID 0bda:0139 Realtek Semiconductor Corp. 
Bus 002 Device 003: ID 04f2:b330 Chicony Electronics Co., Ltd 
Bus 002 Device 004: ID 8087:07da Intel Corp. 
Bus 003 Device 009: ID 2109:0811  
Bus 004 Device 013: ID 17e9:4305 Newnham Research 
Bus 004 Device 014: ID 2109:0811  

```

and hwinfo spits out this
```
  usb device: name = 4-1.1:1.0
    path = /devices/pci0000:00/0000:00:14.0/usb4/4-1/4-1.1/4-1.1:1.0
    modalias = "usb:v17E9p4305d0015dcEFdsc02dp01icFFisc00ip03"
    bInterfaceNumber = 0
    bInterfaceClass = 255
    bInterfaceSubClass = 0
    bInterfaceProtocol = 3
    if: 4-1.1:1.0 @ /devices/pci0000:00/0000:00:14.0/usb4/4-1/4-1.1
    bDeviceClass = 239
    bDeviceSubClass = 2
    bDeviceProtocol = 1
    idVendor = 0x17e9
    idProduct = 0x4305
    manufacturer = "DisplayLink"
    product = "dynadock U3.0"
    serial = "10003171"
    bcdDevice = 0015
    speed = "5000"
  usb device: name = 4-1.1:1.1
    path = /devices/pci0000:00/0000:00:14.0/usb4/4-1/4-1.1/4-1.1:1.1
    modalias = "usb:v17E9p4305d0015dcEFdsc02dp01icFEisc01ip01"
    bInterfaceNumber = 1
    bInterfaceClass = 254
    bInterfaceSubClass = 1
    bInterfaceProtocol = 1
    if: 4-1.1:1.1 @ /devices/pci0000:00/0000:00:14.0/usb4/4-1/4-1.1
    bDeviceClass = 239
    bDeviceSubClass = 2
    bDeviceProtocol = 1
    idVendor = 0x17e9
    idProduct = 0x4305
    manufacturer = "DisplayLink"
    product = "dynadock U3.0"
    serial = "10003171"
    bcdDevice = 0015
    speed = "5000"
  usb device: name = 4-1.1:1.2
    path = /devices/pci0000:00/0000:00:14.0/usb4/4-1/4-1.1/4-1.1:1.2
    modalias = "usb:v17E9p4305d0015dcEFdsc02dp01ic01isc01ip20"
    bInterfaceNumber = 2
    bInterfaceClass = 1
    bInterfaceSubClass = 1
    bInterfaceProtocol = 32
    if: 4-1.1:1.2 @ /devices/pci0000:00/0000:00:14.0/usb4/4-1/4-1.1
    bDeviceClass = 239
    bDeviceSubClass = 2
    bDeviceProtocol = 1
    idVendor = 0x17e9
    idProduct = 0x4305
    manufacturer = "DisplayLink"
    product = "dynadock U3.0"
    serial = "10003171"
    bcdDevice = 0015
    speed = "5000"
  usb device: name = 4-1.1:1.3
    path = /devices/pci0000:00/0000:00:14.0/usb4/4-1/4-1.1/4-1.1:1.3
    modalias = "usb:v17E9p4305d0015dcEFdsc02dp01ic01isc02ip20"
    bInterfaceNumber = 3
    bInterfaceClass = 1
    bInterfaceSubClass = 2
    bInterfaceProtocol = 32
    if: 4-1.1:1.3 @ /devices/pci0000:00/0000:00:14.0/usb4/4-1/4-1.1
    bDeviceClass = 239
    bDeviceSubClass = 2
    bDeviceProtocol = 1
    idVendor = 0x17e9
    idProduct = 0x4305
    manufacturer = "DisplayLink"
    product = "dynadock U3.0"
    serial = "10003171"
    bcdDevice = 0015
    speed = "5000"
  usb device: name = 4-1.1:1.4
    path = /devices/pci0000:00/0000:00:14.0/usb4/4-1/4-1.1/4-1.1:1.4
    modalias = "usb:v17E9p4305d0015dcEFdsc02dp01ic01isc02ip20"
    bInterfaceNumber = 4
    bInterfaceClass = 1
    bInterfaceSubClass = 2
    bInterfaceProtocol = 32
    if: 4-1.1:1.4 @ /devices/pci0000:00/0000:00:14.0/usb4/4-1/4-1.1
    bDeviceClass = 239
    bDeviceSubClass = 2
    bDeviceProtocol = 1
    idVendor = 0x17e9
    idProduct = 0x4305
    manufacturer = "DisplayLink"
    product = "dynadock U3.0"
    serial = "10003171"
    bcdDevice = 0015
    speed = "5000"
  usb device: name = 4-1.1:1.5
    path = /devices/pci0000:00/0000:00:14.0/usb4/4-1/4-1.1/4-1.1:1.5
    modalias = "usb:v17E9p4305d0015dcEFdsc02dp01ic02isc06ip00"
    bInterfaceNumber = 5
    bInterfaceClass = 2
    bInterfaceSubClass = 6
    bInterfaceProtocol = 0
    if: 4-1.1:1.5 @ /devices/pci0000:00/0000:00:14.0/usb4/4-1/4-1.1
    bDeviceClass = 239
    bDeviceSubClass = 2
    bDeviceProtocol = 1
    idVendor = 0x17e9
    idProduct = 0x4305
    manufacturer = "DisplayLink"
    product = "dynadock U3.0"
    serial = "10003171"
    bcdDevice = 0015
    speed = "5000"
  usb device: name = 4-1.1:1.6
    path = /devices/pci0000:00/0000:00:14.0/usb4/4-1/4-1.1/4-1.1:1.6
    modalias = "usb:v17E9p4305d0015dcEFdsc02dp01ic0Aisc00ip00"
    bInterfaceNumber = 6
    bInterfaceClass = 10
    bInterfaceSubClass = 0
    bInterfaceProtocol = 0
    if: 4-1.1:1.6 @ /devices/pci0000:00/0000:00:14.0/usb4/4-1/4-1.1
    bDeviceClass = 239
    bDeviceSubClass = 2
    bDeviceProtocol = 1
    idVendor = 0x17e9
    idProduct = 0x4305
    manufacturer = "DisplayLink"
    product = "dynadock U3.0"
    serial = "10003171"
    bcdDevice = 0015
    speed = "5000"

```

any ideas? ive already tried the displaylink drivers in ubuntus software manager.

im not above PayPal-ing someone $50 if they can get all 3 monitors in extended desktop mode :)

---

### Post by albandy on 2012-08-16
This can help:
[http://broddlit.wordpress.com/2009/10/27/dynadock-displaylink-under-linux/](http://broddlit.wordpress.com/2009/10/27/dynadock-displaylink-under-linux/)

---

### Post by pborges on 2012-08-16
thanks for the link, but i already have 
[http://packages.ubuntu.com/precise/xserver-xorg-video-displaylink](http://packages.ubuntu.com/precise/xserver-xorg-video-displaylink)
installed and it didnt seem to help any but to be honest i have never been to good with Xorg stuff...

---

### Post by mschering on 2012-08-31
I have a dynadock u3 myself now. 

I don't get any video output as well. Did you manage to get the video to work?

---

### Post by Rocko262c on 2012-12-11
Dear Everyone,

I am in the same boat. I have a Portege Z930 and a DynaDock and it doesn't work in Ubuntu.

Any help is greatly appreciated.

Cheers,
Rocko262c

---

### Post by bruceforsberg on 2013-01-10
Same here. Just got a Toshiba Portege R835 with USB dock. Need same.

---

### Post by stek666 on 2013-01-29
Hi,
there is any solution for that?

I have a Samsung ultrabook and I want to use them with ubuntu.
But I need to be able to use my dynadock 3.0.


regards
Stefano

---

### Post by stek666 on 2013-01-29
I tried many way, but it seams impossible to install xserver-xorg-video-displaylink on the last ubuntu version.

If there is no way, I have to goes back in Windows7..

Stefano
[B]
[/B]

---

### Post by tribaal on 2013-01-31
Same boat - I'd love to use my dynadock on Ubuntu!

If only Toshiba didn't have such abysmal support for linux... :(

- Trib'

---

### Post by stek666 on 2013-01-31
I posted this on the toshiba support forum: [http://forums.computers.toshiba-europe.com/forums/thread.jspa?threadID=70517](http://forums.computers.toshiba-europe.com/forums/thread.jspa?threadID=70517)
It world be nice you will comment the request too.


Stefano

---

### Post by Rocko262c on 2013-02-23
Dear Everyone,

I have updated/ect. Ubuntu and somehow the dynadock was able to port the network to the computer. No idea how that magically happened or what update that occurred on.  I have been running Ubuntu 12.10 since I have been using the dynadock.

I am still unable to use the external monitor with this device and how frustrating this is.

Here are some forums that people are trying to figure this out, but no solutions yet (February 24, 2013):
[http://ubuntuforums.org/archive/index.php/t-1521329.html](http://ubuntuforums.org/archive/index.php/t-1521329.html)
[http://askubuntu.com/questions/248388/ubuntu-toshiba-dynadock-u3-0](http://askubuntu.com/questions/248388/ubuntu-toshiba-dynadock-u3-0)

I would suggest that we keep our fingers crossed and hope that we get some much needed DISPLAY support for this device.

Cheers,
Rocko262c

---

### Post by s-p-constantine on 2014-01-07
> **Rocko262c said:**
> Dear Everyone,

I have updated/ect. Ubuntu and somehow the dynadock was able to port the network to the computer. No idea how that magically happened or what update that occurred on.  I have been running Ubuntu 12.10 since I have been using the dynadock.

I am still unable to use the external monitor with this device and how frustrating this is.

Here are some forums that people are trying to figure this out, but no solutions yet (February 24, 2013):
[http://ubuntuforums.org/archive/index.php/t-1521329.html](http://ubuntuforums.org/archive/index.php/t-1521329.html)
[http://askubuntu.com/questions/248388/ubuntu-toshiba-dynadock-u3-0](http://askubuntu.com/questions/248388/ubuntu-toshiba-dynadock-u3-0)

I would suggest that we keep our fingers crossed and hope that we get some much needed DISPLAY support for this device.

Cheers,
Rocko262c

I have sound and USB, but no video or network.

The network is the killer for me - it worked on my Dynadock U10, but not with the U3.0... :-(

Any ideas? (I have 12.04)

EDIT: scratch that - I wasn't using the supplied USB A-to-B cable. Network is fine now.

---

### Post by s-p-constantine on 2014-01-10
> **albandy said:**
> This can help:
[http://broddlit.wordpress.com/2009/10/27/dynadock-displaylink-under-linux/](http://broddlit.wordpress.com/2009/10/27/dynadock-displaylink-under-linux/)

I went here:[http://broddlit.wordpress.com/2009/10/27/dynadock-displaylink-under-linux/](http://broddlit.wordpress.com/2009/10/27/dynadock-displaylink-under-linux/)

I then did this: [http://libdlo.freedesktop.org/wiki/displaylink-mod/](http://libdlo.freedesktop.org/wiki/displaylink-mod/)

followed by this: [http://libdlo.freedesktop.org/wiki/xf86-driver-displaylink/](http://libdlo.freedesktop.org/wiki/xf86-driver-displaylink/)

And now my 12.04 boots to a black screen.

How do I undo the steps above to get my system back to the way to was..? ( I can live without the Dynadock display!!)

Many thanks - Steven.

---

### Post by s-p-constantine on 2014-01-10
> **s-p-constantine said:**
> I went here:[http://broddlit.wordpress.com/2009/10/27/dynadock-displaylink-under-linux/](http://broddlit.wordpress.com/2009/10/27/dynadock-displaylink-under-linux/)

I then did this: [http://libdlo.freedesktop.org/wiki/displaylink-mod/](http://libdlo.freedesktop.org/wiki/displaylink-mod/)

followed by this: [http://libdlo.freedesktop.org/wiki/xf86-driver-displaylink/](http://libdlo.freedesktop.org/wiki/xf86-driver-displaylink/)

And now my 12.04 boots to a black screen.

How do I undo the steps above to get my system back to the way to was..? ( I can live without the Dynadock display!!)

Many thanks - Steven.

SOLVED:
 sudo dpkg-reconfigure xerver-xorg

---

### Post by Rocko262c on 2014-05-26
It has been since 2012, has anyone been able to get this device to work with the monitor?
Cheers,
Rocko262c

---

