---
title: "Logitech Cordless MediaBoard Pro bluetooth keyboard+touchpad problem"
date: 2010-02-23
forum: Hardware
---

### Post by Eldis on 2010-02-23
I've recently bought this LOGITECH CORDLESS MEDIABOARD PRO FOR PS3
and I'm using it on my ubuntu (karmic) htpc. I have managed to pair and trust the device with blueman but after some idle it somehow stops working. I can use the reset button on the buttom and do hidd --search or sudo hidd --connect <hw address> to get it working again for a short period.

I would like to get it working more permanently there is also an on/off switch on the keyboard to save battery power so it would be nice if I could turn it off and back on and it would reconnect and work.

from dmesg:
```
[186527.462828] input: Logitech Cordless MediaBoard Pro(TM) as /devices/pci0000:00/0000:00:1d.2/usb7/7-1/7-1:1.0/bluetooth/hci0/hci0:102/input25
[186527.462936] generic-bluetooth 0005:046D:B30A.0013: input,hidraw6: BLUETOOTH HID v1.1b Mouse [Logitech Cordless MediaBoard Pro(TM)] on 00:15:83:15:A3:10
[186852.378916] input: Logitech Cordless MediaBoard Pro(TM) as /devices/pci0000:00/0000:00:1d.2/usb7/7-1/7-1:1.0/bluetooth/hci0/hci0:112/input26
[186852.379027] generic-bluetooth 0005:046D:B30A.0014: input,hidraw6: BLUETOOTH HID v1.1b Mouse [Logitech Cordless MediaBoard Pro(TM)] on 00:15:83:15:A3:10
```

So everytime I reconnect it it gets a new input number that might have something to do with the problem but I'm not sure.

---

### Post by andersja on 2010-11-01
> **Eldis said:**
> So everytime I reconnect it it gets a new input number that might have something to do with the problem but I'm not sure.

If you are still affected by this bug under Lucid/Maverick, see this link for more information about how to submit debugging information to the developers:
[https://help.ubuntu.com/community/ReportingBugs]("https://help.ubuntu.com/community/ReportingBugs")
[https://help.ubuntu.com/community/ReportingBugs#Adding%20Apport%20Debug%20Information%20to%20an%20Existing%20Launchpad%20Bug]("https://help.ubuntu.com/community/ReportingBugs#Adding%20Apport%20Debug%20Information%20to%20an%20Existing%20Launchpad%20Bug")

It could be [this bug (#292042)]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/292042"), but please verify and post a new bug if necessary.

---

### Post by Eldis on 2010-11-01
Unfortunately I sold the keyboard since it didn't work the way I wanted but I'll try to submit bug reports in the future if and when I encounter them.

---

