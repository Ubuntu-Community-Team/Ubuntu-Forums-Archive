---
title: "Xpad drivers and third party controllers?"
date: 2011-10-01
forum: Hardware
---

### Post by Victoryofthepeople on 2011-10-01
I just bought a Razer Onza Xbox 360 controller for my PC and it appers  like it isn't detected properly by linux. I tried using joypad  configuration tools and the alternative xboxdrv driver, but it didn't  help.
 
 I tried running lsusb to see if the controller was detected al all and here's what I found:
 > 
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 **Bus 002 Device 004: ID 1689:fd00 **
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 Bus 001 Device 004: ID 05e3:0760 Genesys Logic, Inc. USB 2.0 Card Reader/Writer
 Bus 001 Device 003: ID 1058:0704 Western Digital Technologies, Inc. Passport External HDD
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
  Even weirder, on Windows, the controller is detected fine out of the box and runs with the generic Xbox 360 drivers.
 
 Any help on where I should report this bug or what I can do to work arround it?

---

### Post by Victoryofthepeople on 2011-10-03
Bump. I'd really like an advice or something.

---

### Post by Victoryofthepeople on 2011-10-09
Double bump.It's nice being able to play on Windows, but  I'd still like to be able to use that controller on my main box.

---

### Post by benmoran on 2011-10-14
I would send an email to Grumbel, the guy who created xboxdrv. I'm sure he'll be able to help you out. He would probably like to add support for that usb id to the driver anyway.

In the mean time, you can give the usb id directly to xboxdrv in this way:

xboxdrv --device-by-id 1689:fd00 --type xbox360

---

### Post by Victoryofthepeople on 2011-10-16
> **benmoran said:**
> I would send an email to Grumbel, the guy who created xboxdrv. I'm sure he'll be able to help you out. He would probably like to add support for that usb id to the driver anyway.

In the mean time, you can give the usb id directly to xboxdrv in this way:

xboxdrv --device-by-id 1689:fd00 --type xbox360
Woah!
The devs really think of everything!
Thanks a lot!

---

