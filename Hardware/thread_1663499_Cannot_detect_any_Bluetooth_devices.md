---
title: "Cannot detect any Bluetooth devices"
date: 2011-01-09
forum: Hardware
---

### Post by runt on 2011-01-09
Ok, I got a free Dell Inspiron B130 while at my parents this weekend.  I decided I would plug it one of my micro Bluetooth adpaters once I got home and made sure the laptop worked fine (Windows couldn't deal with the HD for some reason but Ubuntu works fine).  I tried 10.10 first and all was well until I tried to pair my Bluetooth Mouse (a Rocketfish Apple Bluetooth Mouse).  Didn't work so then I tried my phone and it can't pair either.  I rolled back to 10.04 to see if it was a bug in 10.10 and that made no difference.  My adapter is detected fine and I am putting the items into pairing mode before I try to.

Here is the output of lsusb
```
shaun@Crianna:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 008: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```Anyone have some ideas on what I should look at to get it working?

---

### Post by runt on 2011-01-10
Ok,
 
Tried my other bluetooth adapter when I got to work and it works now.  No clue but its solved.

---

