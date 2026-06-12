---
title: "Sigma cam 4300????"
date: 2010-09-24
forum: Hardware
---

### Post by teolandon on 2010-09-24
So, how can I get this thing working? I've plugged it in, but it ain't workin'. Plz, someone help me.:(

---

### Post by gordintoronto on 2010-09-24
Did you check whether it is supported before you bought it?

I tried to Google: sigma cam 4300 linux
but the first few responses were not useful.

From Accessories/Terminal you can enter the command:
lsusb

which will list your USB devices. For example, on my system this line appears:
Bus 004 Device 002: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 Webcam

Oddly, the most useful part of that line is "0ac8:303b" which is the true identity of the device.

---

### Post by teolandon on 2010-09-26
> **gordintoronto said:**
> Did you check whether it is supported before you bought it?

I tried to Google: sigma cam 4300 linux
but the first few responses were not useful.

From Accessories/Terminal you can enter the command:
lsusb

which will list your USB devices. For example, on my system this line appears:
Bus 004 Device 002: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 Webcam

Oddly, the most useful part of that line is "0ac8:303b" which is the true identity of the device.
So, the PC detects the camera, firstly, because I can use it as a microphone, and secondly, because:

root@teolandon-desktop:/home/teolandon# lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 062a:3271 Creative Labs 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0ad2:931c Service & Quality Technology Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

, where the 0ad2:931c is my camera.

So, what do I do now?

---

### Post by teolandon on 2010-09-26
> **gordintoronto said:**
> Did you check whether it is supported before you bought it?

I tried to Google: sigma cam 4300 linux
but the first few responses were not useful.

From Accessories/Terminal you can enter the command:
lsusb

which will list your USB devices. For example, on my system this line appears:
Bus 004 Device 002: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 Webcam

Oddly, the most useful part of that line is "0ac8:303b" which is the true identity of the device.
So, the PC detects the camera, firstly, because I can use it as a microphone, and secondly, because:

root@teolandon-desktop:/home/teolandon# lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 062a:3271 Creative Labs 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0ad2:931c Service & Quality Technology Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

, where the 0ad2:931c is my camera.

So, what do I do now?

---

### Post by gordintoronto on 2010-09-26
Wow, I would have guessed that the Creative Labs line was a webcam.

I think your best bet is to put the webcam on eBay and search for one which is supported.

I have a couple of webcams which are no longer supported in Windows, and certainly are not supported in Linux, so it's an area where "buyer beware" applies.

---

