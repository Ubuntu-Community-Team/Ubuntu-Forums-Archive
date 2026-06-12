---
title: "Hardware in a Motion Computing C5 (or, where's my bluetooh?)"
date: 2013-05-09
forum: Hardware
---

### Post by supremedalek on 2013-05-09
I have a Motion Computing C5 in which I installed ubuntu 12.04 in. And now I am trying to configure its hardware so I can use it. Right now I have the wireless and the pen working well enough to use it, but that is pretty much it. This tablet is supposed to have a camera, a finger scanner, a rfid thingie, and most importantly (to me) bluetooth (I could use a keyboard since tapping on the screen is a bit of a drag). Most of those I have not been able to see in dmesg. 

Well, I saw the following messages in dmesg:
	
```
[   16.276814] init: failsafe main process (679) killed by TERM signal^M
[   19.967815] ppdev: user-space parallel port driver^M
[   20.636963] Bluetooth: Core ver 2.16^M
[   20.637088] NET: Registered protocol family 31^M
[   20.637092] Bluetooth: HCI device and connection manager initialized^M
[   20.638092] Bluetooth: HCI socket layer initialized^M
[   20.638099] Bluetooth: L2CAP socket layer initialized^M
[   20.638113] Bluetooth: SCO socket layer initialized^M
[   20.983391] Bluetooth: RFCOMM TTY layer initialized^M
[   20.983402] Bluetooth: RFCOMM socket layer initialized^M
[   20.983405] Bluetooth: RFCOMM ver 1.11^M
[   21.191575] Bluetooth: BNEP (Ethernet Emulation) ver 1.3^M
[   21.191583] Bluetooth: BNEP filters: protocol multicast^M
```

but does that the OS saw the bluetooth device? If so, why am I not able to use it? What should I be looking for using lspci, lsusb, or dmidecode (so I can post something useful here)?

---

### Post by gordintoronto on 2013-05-10
Just run lspci and post the output, it should be less than 20 lines.

How did you get Ubuntu installed, with no CD and no USB ports?

---

### Post by grahammechanical on 2013-05-10
It should have 3 USB 2 ports in a docking station

[http://ruggedpcreview.com/3_slates_motion_c5.html](http://ruggedpcreview.com/3_slates_motion_c5.html)

Did System Settings>Bluetooth not do anything for you?

Regards.

---

