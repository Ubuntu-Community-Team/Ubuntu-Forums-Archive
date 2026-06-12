---
title: "Microsoft VX-5000 webcam no longer working"
date: 2010-09-12
forum: Hardware
---

### Post by zck on 2010-09-12
In the past, I've used my Microsoft VX-5000 webcam on Skype, but I'm having problems with that now. When I've used it before, I turned it on and off using a GUI in System>Preferences, or System>Administration, but I can't find the proper option there now. I checked the items in the Main Menu editor, and there isn't anything listed but not shown that would allow me to enable my webcam. I don't think I've used the webcam since updating to 10.4, but I may be wrong.

lsusb reports:

> Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 17f6:0709 Unicomp, Inc 
Bus 004 Device 002: ID 045e:0724 Microsoft Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:0724 Microsoft Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 045e:0728 Microsoft Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubLooking in lsusb -v | less  indicates that the webcam is this entry:

Bus 001 Device 002: ID 045e:0728 Microsoft Corp.

The other Microsoft entries are other hardware.

When I first tried this today, Skype was able to get sound (using the "test call" feature in its preferences), but not video. Now, it won't do either. The blue light on the webcam isn't turning on, but it did when the audio was working.

Any help would be greatly appreciated.

---

### Post by AHoneybun on 2011-03-14
I have the same camera but the audio is not working for any service, I have not tried skype. But Google chat and CHeese booth it does not work.

---

