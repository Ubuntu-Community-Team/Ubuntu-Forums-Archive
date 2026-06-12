---
title: "why is Xsane trying to scan from my tv card?"
date: 2009-02-18
forum: Hardware
---

### Post by 37fleetwood on 2009-02-18
why is it trying to scan from the tv card rather than the scanner? is there a way to change this? it shouldn't ever use this device to my feeling. I haven't figured out how to get it to recognize the scanner, I just got a new one and it doesn't seem to find it like it did the other one of the same brand and a similar model. I have a Canon MP 190.
thanks
Scott

---

### Post by geraldm on 2009-02-18
The TV card is a framing device,  and it can provide a picture.  XSane may grab a picture when instructed to, from known devices.

MP 190 is not supported as far as scanning.  Canon has some that are supported.

Usually the way xsane can find a scanner device is that the device has group permissions of rw- and the group name is "scanner".  

Gerald

---

