---
title: "Put drive from one laptop in an other - boot errors"
date: 2010-11-27
forum: Hardware
---

### Post by Resurge on 2010-11-27
I took my SSD from my one laptop and put it in a different one.
Grub still works fine, and Windows 7 installed all the drivers of the new laptop perfectly.

Ubuntu however won't boot.
Notable errors I'm getting:
* Starting the Firestarter firewall...
    wlan0: error fetching interface information: Device not found
    wlan0: error fetching interface information: Device not found
    wlan0: error fetching interface information: Device not found [fail]
* Not starting jetty edit /etc/default/jetty and change NO_START to be 0 (or comment it out)

And the last line (after which the laptop seems to be stuck):
* Starting DHCP server dhcp3
[[image]]("http://imgur.com/QlkbU.jpg")

Also, trying safe mode just gives a black screen.
In both normal boot and safe mode the power button still works and the laptop will give some messages and shut down.

The laptop I'm coming from is an asus f3sv 0-18c, and the new one is a dell latitude D630
I already tried a live cd and ubuntu seems to boot fine there.

Edit: just noticed I can also switch between err.. terminals? (ctrl+F1, F2,..)
Edit2: Aha! :D
After figuring out edit1 I could remove the x11 config file. Now everything works smoothly again :) (except for some expected driver problems which are an entirely different problem to figure out)
Hm, apparently I can't change the tag to SOLVED myself?

---

### Post by dino99 on 2010-11-27
grub works with uuid, each time a device is plugged/unplugged you get new uuid

so you need to upgrade grub

sudo blkid
( to get the uuid)

sudo update-grub
(to update with the good uuid

about the network issue you might check driver activation and errors logged to know about that chipset

---

