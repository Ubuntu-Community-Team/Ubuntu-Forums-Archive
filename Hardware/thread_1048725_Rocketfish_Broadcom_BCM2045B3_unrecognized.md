---
title: "Rocketfish Broadcom BCM2045B3 unrecognized"
date: 2009-01-23
forum: Hardware
---

### Post by Fata_ku on 2009-01-23
I know this question has been gone over several times before and I'm sorry to be asking it again, but I am at my wits' end with this.

I bought (some time ago) a rocketfish bluetooth dongle (Broadcom BCM2045B3), and my wacom tablet somewhat passes through (treated exactly as a mouse though, with way too much acceleration).

At first I though my bluetooth drivers were the problem, so I got BleuSoleil (which didn't work), Bluez-utils (which didn't work) and KdeBluetooth (which did not work).

I then ran lsusb
```

Bus 001 Device 013: ID 0a5c:4503 Broadcom Corp. 
Bus 001 Device 012: ID 0a5c:4502 Broadcom Corp. 
Bus 001 Device 011: ID 0a5c:4500 Broadcom Corp. 

```

Then hcitool dev, whose only return was
```
Devices:

```

hcitool scan:
```
Device is not available: Address family not supported by protocol
```

sudo hidd --search:
```
Can't open HIDP control socket: Address family not supported by protocol
```

That is where I got stuck...  my device is there, but nothing recognizes it as a bluetooth dongle. I know some people got the same adapter and got it up and running. What can I do to get it working properly? I know it works perfectly on Windows...

I am using a Compaq Presario; 
Ubuntu 8.1 (intrepid)
Kernel Linux 2.6.27-9-generic
GNOME 2.24.1
AMD Athlon 64 dual-core 3800+ processor

---

### Post by Fata_ku on 2009-01-24
I don't usually bump, but i've been continuously looking for the past 5 hours and nothing seems to work.

---

### Post by Fata_ku on 2009-01-24
I've tried everything I could think of. For whoever experiences the same problems here are a few link that might (or might not, like in my case) help.

[http://osdir.com/ml/drivers.wacom/2006-11/msg00022.html](http://osdir.com/ml/drivers.wacom/2006-11/msg00022.html)
[https://help.ubuntu.com/community/WacomGraphireBluetooth](https://help.ubuntu.com/community/WacomGraphireBluetooth)
[http://linuxwacom.sourceforge.net/](http://linuxwacom.sourceforge.net/)

---

### Post by Fata_ku on 2009-01-24
well, the situation somewhat got better:

```

lsusb
Bus 001 Device 014: ID 0a5c:2120 Broadcom Corp. 2045 Bluetooth 2.0 USB-UHE Device with trace filter

```

yet I still have no bluetooth functionnality...

I've been playing around with PyUSB for a small while, and even python can't get into the device. Yet it works perfectly fine on Windows computers. (the dongle that is)

---

### Post by joe_geek on 2009-02-15
I have the same problem. Rocketfish dongle isn't being recognized as a bluetooth device. I haven't been able to figure out what's wrong either. Some people say bluetooth worked for them in Hardy but it brokin Intrepid, but I never got this dongle to work in Hardy before my upgrade to Intrepid.

lsusb -v told me that the 3 Broadcom devices are listed as a mouse, keyboard and hub, but nothing bluetooth.

Any help would be appreciated.

---

### Post by kyroha on 2009-02-16
I have the exact same dongle with the exact problem. The wierd thing is it used to work, and for some reason now when I plug it in it is detected as a USB mouse instead of a bluetooth device. I would think there would have to be some way to tell it to change that behavior but I am at a loss as to what that would be.
from dmesg when I plug it in
> 
[ 1538.708025] usb 3-2: new full speed USB device using uhci_hcd and address 17
[ 1538.916750] usb 3-2: configuration #1 chosen from 1 choice
[ 1538.920212] hub 3-2:1.0: USB hub found
[ 1538.929963] hub 3-2:1.0: 3 ports detected
[ 1539.237638] usb 3-2.2: new full speed USB device using uhci_hcd and address 18
[ 1539.381542] usb 3-2.2: configuration #1 chosen from 1 choice
[ 1539.399942] input: Broadcom Corp BCM2045B3 ROM as /devices/pci0000:00/0000:00:10.2/usb3/3-2/3-2.2/3-2.2:1.0/input/input20
[ 1539.428336] input,hidraw3: USB HID v1.11 Keyboard [Broadcom Corp BCM2045B3 ROM] on usb-0000:00:10.2-2.2
[ 1539.505302] usb 3-2.3: new full speed USB device using uhci_hcd and address 19
[ 1539.671325] usb 3-2.3: configuration #1 chosen from 1 choice
[ 1539.689016] input: Broadcom Corp BCM2045B3 ROM as /devices/pci0000:00/0000:00:10.2/usb3/3-2/3-2.3/3-2.3:1.0/input/input21
[ 1539.720325] input,hidraw4: USB HID v1.11 Mouse [Broadcom Corp BCM2045B3 ROM] on usb-0000:00:10.2-2.3

and from lsusb
> 
Bus 003 Device 019: ID 0a5c:4503 Broadcom Corp. 
Bus 003 Device 018: ID 0a5c:4502 Broadcom Corp. 
Bus 003 Device 017: ID 0a5c:4500 Broadcom Corp. 

Whats driving me crazy is this was literally working fine 12 hours ago and I have no idea what changed. One second the system was seeing it as a bluetooth dongle and then it sees it as a USB mouse and keyboard, very frustrating.

---

### Post by cta16 on 2009-02-16
I've had trouble getting my Rocketfish BT dongle to work too. Here's a list of BT dongles that work on linux for sure:
[http://www.wiili.org/index.php/Compatible_Bluetooth_Devices]("http://www.wiili.org/index.php/Compatible_Bluetooth_Devices")

---

### Post by C.B.Leslie on 2009-07-01
I have the exact same adaptor. This worked for me:

It must be plugged in from boot:
```
sudo hciconfig hci0 reset
```

---

