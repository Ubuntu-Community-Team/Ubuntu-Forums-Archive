---
title: "composite usb mouse not supported at startup"
date: 2006-06-04
forum: Hardware &amp; Laptops
---

### Post by lapsey on 2006-06-04
i have a usb keyboard with 2 pointing devices. i only want one, in actuality, but the one i want to use does not work unless i cycle the usb port

```
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 004: ID 06cb:0009 Synaptics, Inc. Composite TouchPad and TrackPoint
Bus 003 Device 003: ID 04b3:3019 IBM Corp.
Bus 003 Device 002: ID 04b3:3016 IBM Corp. UltraNav Keyboard Hub
Bus 003 Device 001: ID 0000:0000
# here is where i unplugged/plugged the keyboard back in
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 007: ID 06cb:0009 Synaptics, Inc. Composite TouchPad and TrackPoint
Bus 003 Device 006: ID 04b3:3019 IBM Corp.
Bus 003 Device 005: ID 04b3:3016 IBM Corp. UltraNav Keyboard Hub
Bus 003 Device 001: ID 0000:0000
```
and now both mice work!


is there any way to fix this or cycle the port on the commandline? It's rather annoying and god help users that have this composite device built into their laptop (as many thinkpads do)

---

### Post by lapsey on 2006-11-16
bumping this because the issue has not been resolved for nearly a year!

It worked fine in breezy ](*,)

screenshot of device manager: [http://ubuntuforums.org/attachment.php?attachmentid=6578&d=1141250461](http://ubuntuforums.org/attachment.php?attachmentid=6578&d=1141250461)

---

