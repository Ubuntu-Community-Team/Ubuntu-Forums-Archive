---
title: "dvb-t usb dongle"
date: 2012-12-16
forum: Hardware
---

### Post by GreenBrother on 2012-12-16
Hi, my USB stick is like madman's stick "DVBT USB DONGLE", but I can't use it. I tried all, but i think, that i haven't the correct kernel. Can someone help me?

---

### Post by sanderj on 2012-12-16
> **GreenBrother said:**
> Hi, my USB stick is like madman's stick "DVBT USB DONGLE", but I can't use it. I tried all, but i think, that i haven't the correct kernel. Can someone help me?


With the stick plugged in, post the output of

```
lsusb

lsb_release -a

```

---

### Post by GreenBrother on 2012-12-16
> **sanderj said:**
> With the stick plugged in, post the output of

```
lsusb

lsb_release -a

```
Bus 001 Device 002: ID 046d:0825 Logitech, Inc. Webcam C270
Bus 001 Device 003: ID 15a4:9016 Afatech Technologies, Inc. AF9015 DVB-T USB2.0 stick
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Distributor ID:    Ubuntu
Description:    Ubuntu 12.10
Release:    12.10
Codename:    quantal

---

### Post by sanderj on 2012-12-16
> **GreenBrother said:**
> Distributor ID:    Ubuntu
Description:    Ubuntu 12.10
Release:    12.10
Codename:    quantal

Please read my post carefully ... two commands...

---

### Post by GreenBrother on 2012-12-16
> **sanderj said:**
> With the stick plugged in, post the output of

```
lsusb

lsb_release -a

```

> **sanderj said:**
> Please read my post carefully ... two commands...

Yes, I have edited.

---

### Post by sanderj on 2012-12-16
"AF9015"? That sounds well-known. At with your uptodate Ubuntu, I would expect it to work.

Next step:

Unplug the usb-stick, wait 3 seconds, plug the usb-stick in, and then type:

```
dmesg

```
Post the last 15 lines from dmesg here.

---

### Post by GreenBrother on 2012-12-16
[   31.004963] wlan0: authenticate with bc:05:43:52:00:e7
[   31.014083] wlan0: send auth to bc:05:43:52:00:e7 (try 1/3)
[   31.016867] wlan0: authenticated
[   31.024038] wlan0: associate with bc:05:43:52:00:e7 (try 1/3)
[   31.050695] wlan0: RX AssocResp from bc:05:43:52:00:e7 (capab=0x411 status=0 aid=6)
[   31.051120] wlan0: associated
[   31.051296] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2315.054394] usb 1-7: USB disconnect, device number 3
[ 2320.248127] usb 1-7: new high-speed USB device number 4 using ehci_hcd
[ 2320.384933] usb 1-7: New USB device found, idVendor=15a4, idProduct=9016
[ 2320.384946] usb 1-7: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 2320.384954] usb 1-7: Product: DVB-T 2
[ 2320.384961] usb 1-7: Manufacturer: Afatech
[ 2320.384968] usb 1-7: SerialNumber: 010101010600001
[ 2320.387294] usb 1-7: dvb_usb_v2: found a 'Afatech AF9015 reference design' in cold state
[ 2320.391208] Afatech DVB-T 2: Fixing fullspeed to highspeed interval: 10 -> 7
[ 2320.391814] input: Afatech DVB-T 2 as /devices/pci0000:00/0000:00:13.5/usb1/1-7/1-7:1.1/input/input12
[ 2320.392574] hid-generic 0003:15A4:9016.0002: input,hidraw0: USB HID v1.01 Keyboard [Afatech DVB-T 2] on usb-0000:00:13.5-7/input1
[ 2320.393610] usb 1-7: dvb_usb_v2: Did not find the firmware file 'dvb-usb-af9015.fw'. Please see linux/Documentation/dvb/ for more details on firmware-problems. Status -2
[ 2320.393617] usb 1-7: dvb_usb_v2: 'Afatech AF9015 reference design' error while loading driver (-2)
[ 2320.393630] usb 1-7: dvb_usb_v2: 'Afatech AF9015 reference design' successfully deinitialized and disconnected

Thi is more, but in case...

---

### Post by sanderj on 2012-12-16
Yep ... as I expected: " Did not find the firmware file 'dvb-usb-af9015.fw'."

The firmware has to be installed. In Ubuntu up to version 12.04, there would be the hardware-icon in the upper right corner for proprietary drivers. Just clicking on it would help you to get it installed.

In Ubuntu 12.10 that feature it not *there* anymore. I believe it moved into the Ubuntu Software Center. Can you start that and if there is an option for proprietary software?

EDIT 


Found it: "To do this, open the Software Sources app via the Dash (or through System Settings) and hit the &#8216;Additional Drivers&#8216; tab."


Can you try that?

---

### Post by GreenBrother on 2012-12-16
I serch "dvb-usb-af9015.fw" but there is nothing.

---

### Post by sanderj on 2012-12-16
> **GreenBrother said:**
> I serch "dvb-usb-af9015.fw" but there is nothing.

Why did you search that?

You should do this:

"To do this, open the Software Sources app via the Dash (or through System Settings) and hit the ‘Additional Drivers‘ tab."

---

### Post by GreenBrother on 2012-12-16
"No properly drivers are in use."

---

### Post by sanderj on 2012-12-16
> **GreenBrother said:**
> ...

"Non-free drivers, as of today, they will be managed through Software Sources or System Settings -> Software Sources -> Additional Drivers tab."

---

### Post by GreenBrother on 2012-12-16
I tried, but it crashed and there is "No properly drivers are in use"

[[IMG]http://storage4.album.bg/04e/screenshot_-_12162012_-_09_51_27_pm_1ded8_30213010.png[/IMG]]("http://www.album.bg/petrucciani/images/30213010/")

---

### Post by GreenBrother on 2012-12-16
I see now ur post. Sory! I understood. I have no lucky today. :)
Thank you for your help!

---

### Post by sanderj on 2012-12-16
> **GreenBrother said:**
> I see now ur post. Sory! I understood. I have no lucky today. :)
Thank you for your help!

So ... does it work now? Can you watch DVB-T TV?

---

### Post by GreenBrother on 2012-12-16
> **sanderj said:**
> So ... does it work now? Can you watch DVB-T TV?
No. All is same. :(

---

### Post by sanderj on 2012-12-16
> **GreenBrother said:**
> No. All is same. :(

When you click on the tab Additional Drivers, is the USB-stick plugged in?

---

### Post by GreenBrother on 2012-12-17
> **sanderj said:**
> When you click on the tab Additional Drivers, is the USB-stick plugged in?
Yeah! But that don't help me. Have you seen my picture?

---

### Post by sanderj on 2012-12-17
OK. Pity.

Can you do:

```
sudo apt-get install linux-firmware-nonfree

```

Reason: firmware is in that package. See:

[http://packages.ubuntu.com/search?searchon=contents&keywords=dvb-usb-af9015.fw&mode=exactfilename&suite=quantal&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=dvb-usb-af9015.fw&mode=exactfilename&suite=quantal&arch=any)

Then reboot, plugin the DVB-T stick, check dmesg.

---

### Post by GreenBrother on 2012-12-17
> **sanderj said:**
> OK. Pity.

Can you do:

```
sudo apt-get install linux-firmware-nonfree

```Reason: firmware is in that package. See:

[http://packages.ubuntu.com/search?searchon=contents&keywords=dvb-usb-af9015.fw&mode=exactfilename&suite=quantal&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=dvb-usb-af9015.fw&mode=exactfilename&suite=quantal&arch=any)

Then reboot, plugin the DVB-T stick, check dmesg.

Yeeeeeah!!! My programm scann in this moment! Thank you so much!

---

