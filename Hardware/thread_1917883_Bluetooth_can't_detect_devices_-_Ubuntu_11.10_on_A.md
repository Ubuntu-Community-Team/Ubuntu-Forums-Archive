---
title: "Bluetooth can't detect devices - Ubuntu 11.10 on Acer Aspire One D257"
date: 2012-01-30
forum: Hardware
---

### Post by sekander94 on 2012-01-30
Tested with 11.10 and 10.04

I am able to turn bluetooth on in the menu bar and set it to visible. However it won't detect any devices (tried with an ipod touch and a laptop, which are able to detect each other).

I could not find any additional drivers.


```
sekander@sekander-Netbook:~$ hcitool dev
Devices:
   hci0    60:D8:19:86:20:44
sekander@sekander-Netbook:~$ hcitool scan
Scanning ...
sekander@sekander-Netbook:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b209 Chicony Electronics Co., Ltd
**Bus 004 Device 002: ID 0489:e03c Foxconn / Hon Hai**
```

The bluetooth device is built in to the netbook.

Any ideas?

---

### Post by Wytze on 2012-01-31
I'm having similar problems as stated above. I used hcidump to see if any traffic was going in/out which was not the case.

hcitool scan gives no result and 'hciconfig -a' correctly lists my device. Also I am able to put the bluetooth device into discovery mode and pair it with my phone. The problem occurs when I try to detect bluetooth devices on my end.

This [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/775648") might be related.

I will try to put the inqmode on 0 to see if that helps -> (Update: Didn't help)
```
sudo hciconfig hci0 inqmode 0
```

Update:

I bought a new/different Bluetooth adapter. (Sitecom USB micro adapter bluetooth 2.1 version)
lsusb states:
```
Bus 005 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
```
With this new device I can detect any bluetooth devices without any problems.
Best 13 euro's I spent this week. :) (Considering the amount of time I invested in trying to fix the problem)

---

### Post by sekander94 on 2012-02-02
I booted off of an Ubuntu 10.04 live cd, and had the same problem.

So if I bought a bluetooth mouse with its own bluetooth usb dongle it should work? Wytze, did you originally have the same adapter?

---

### Post by Wytze on 2012-02-03
No I originally had a usb 1.1 bluetooth dongle. I had the same problem with my Dell built-in bluetooth on my laptop. (Also BT 1.1/1.2) Which all happened to be 'Cambridge Silicon Radio' according to lsusb. I will lookup the exact lines this evening.

I think the problem has something to do with the driver that is being used. lsusb doesn't state '(HCI Mode)' for these devices.
In my case btusb was used with reset=1 (checked with systool -v).

Update 1:
I got my first USB Bluetooth device to detect my phone. I was loading some additional drivers with modprobe and after plugging in my adapter it suddenly worked.

```

ls -l /lib/modules/$(uname -r)/kernel/drivers/bluetooth
modinfo hci_vhci
sudo modprobe hci_vhci
modinfo hci_uart
sudo modprobe hci_uart reset=1

```

Update 2:
It seems to be working now without loading any additional drivers. :? Flabbergasted how or why it suddenly works.
```

Bus 005 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)

```
Strange thing is that it now says '(HCI mode)' where it previously didn't.

Update 3:
Tested it on another pc. Suddenly it is working there too (previously it didn't), without doing anything with drivers. Still flabbergasted. Maybe some firmware reset took place? :?

---

