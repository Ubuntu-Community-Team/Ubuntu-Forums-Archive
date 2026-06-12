---
title: "Mouse (and probrally other input devices) not working"
date: 2009-11-10
forum: Hardware
---

### Post by Lusse on 2009-11-10
Hi forum!

None of my mices seems to work atm but i can see that they are connected by watching `lsusb` and `dmesg`. I can also watch the inputs from them in realtime bby doing `sudo less -f /dev/inout/mouse2`. The strange thing is that my touchpad works as normal. This affects bluetoothmices aswell.

The logical thing to asume would be that a upgrade of some package caused this, below is an attached log of my last `sudo apt-get dist-upgrade`.

Cheers, Linus Unnebäck.

---

