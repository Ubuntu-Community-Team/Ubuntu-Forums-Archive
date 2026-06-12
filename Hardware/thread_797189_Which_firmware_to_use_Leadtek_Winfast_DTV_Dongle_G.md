---
title: "Which firmware to use Leadtek Winfast DTV Dongle Gold with 8.04 ?"
date: 2008-05-17
forum: Hardware
---

### Post by Mooks on 2008-05-17
Hi,

What firmware am I suppose to use to get the Leadtek Winfast DTV Dongle Gold to recognise properly as a tv stick ?  I've tried using the dvb-usb-dib0700-01.fw firmware and haven't had much success yet.

cheers,

Mooks

---

### Post by teaker1s on 2008-05-17
just a quick google and I found this
[http://www.linuxtv.org/wiki/index.php/Leadtek_Winfast_DTV_Dongle]("http://www.linuxtv.org/wiki/index.php/Leadtek_Winfast_DTV_Dongle")
seconly have you ```
lsusb
``` and tried to find info with vendor and product id?

---

### Post by tlli on 2008-06-19
Hi,
Has anybody got this dvb card working with Ubuntu (8.04)?
The card seems to be recognised at boot up, but no /dev/dvb directory is created.

I have looked at linuxtv.org, but the cards identified there have id's of:
* 0413:6f00
* 0413:6f01

The Gold dongle is identifed as:
0413:6029

Any help would be greatly appreciated.
Thank you.

dmesg output:
[ 734.780212] input: Leadtek WinFast DTV Dongle Gold as /devices/pci0000:00/0000:00:1d.7/usb5/5-1/5-1:1.1/input/input12
[ 734.808435] input,hidraw0: USB HID v1.01 Keyboard [Leadtek WinFast DTV Dongle Gold] on usb-0000:00:1d.7-1

---

### Post by STYX2009 on 2009-05-29
**Leadtek DTV Dongle Gold [**0413:6029**] uses AFA AF9015.**
**Here is the AF9015 firmware :**
[http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.95.0/dvb-usb-af9015.fw](http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/4.95.0/dvb-usb-af9015.fw)
 
[http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/](http://www.otit.fi/~crope/v4l-dvb/af9015/af9015_firmware_cutter/firmware_files/)

---

