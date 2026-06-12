---
title: "USB Wireless card (drivers installed with NDISWrapper) not automounting"
date: 2008-08-25
forum: Hardware
---

### Post by hbah427 on 2008-08-25
hey everybody, i thought I'd move from "Absolute Beginner" to the Main forum.

well, I just made the big leap (i know i know) from Gutsy to Hardy. Little bit of a shaky installation though. Anyway! after I upgraded, I noticed my wireless card's LED was not on at all. I have 2 in my house (one under XP) so i tired the other one. same.

i did lsusb

This is with it plugged in

```
hbah427@Harlans-computer:/$ lsusb
Bus 004 Device 026: ID 05ac:1291 Apple Computer, Inc. 
Bus 004 Device 025: ID 050d:805c **Belkin Components **
Bus 004 Device 006: ID 046d:c211 Logitech, Inc. iTouch Cordless Reciever
Bus 004 Device 005: ID 058f:9254 Alcor Micro Corp. Hub
Bus 004 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 003 Device 001: ID 0000:0000 
Bus 002 Device 002: ID 046d:c50b Logitech, Inc. Cordless Desktop Optical
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```

This is when I unplugged it

```
hbah427@Harlans-computer:/$ lsusb
Bus 004 Device 026: ID 05ac:1291 Apple Computer, Inc. 
Bus 004 Device 006: ID 046d:c211 Logitech, Inc. iTouch Cordless Reciever
Bus 004 Device 005: ID 058f:9254 Alcor Micro Corp. Hub
Bus 004 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c50b Logitech, Inc. Cordless Desktop Optical
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

This is when i plugged it BACK in

```
hbah427@Harlans-computer:/$ lsusb 
Bus 004 Device 027: ID 050d:805c **Belkin Components** 
Bus 004 Device 026: ID 05ac:1291 Apple Computer, Inc. 
Bus 004 Device 006: ID 046d:c211 Logitech, Inc. iTouch Cordless Reciever
Bus 004 Device 005: ID 058f:9254 Alcor Micro Corp. Hub
Bus 004 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c50b Logitech, Inc. Cordless Desktop Optical
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
hbah427@Harlans-computer:/$ 
```

so, I do know my computer is recognizing this, but not mounting it for some odd reason...

oh, and I had to use windows to upload this.
boooooooooo

3 days with no answers???

---

