---
title: "SelfIDs failed root check FireWire (IEEE 1394)"
date: 2007-01-23
forum: Hardware &amp; Laptops
---

### Post by kjells on 2007-01-23
I can't get my DVCam to work using firewire. It seems to be a problem with my firewire (Texas Instruments OHCI Compliant IEEE 1394). 

Syslog report this:
Jan 23 18:22:48 localhost kernel: [17180045.192000] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
Jan 23 18:22:48 localhost kernel: [17180045.192000] ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[0080458020964134]

Jan 23 18:36:31 localhost kernel: [17180867.572000] ieee1394: Node resumed: ID:BUS[0-00:1023]  GUID[0080458020964134]
Jan 23 18:36:31 localhost kernel: [17180867.572000] ieee1394: Node changed: 0-00:1023 -> 0-01:1023
Jan 23 18:36:44 localhost kernel: [17180881.184000] ieee1394: Node changed: 0-01:1023 -> 0-00:1023
Jan 23 18:36:44 localhost kernel: [17180881.184000] ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[0080458020964134].

I get a repeated error message from dmseg that partly contain:

[17179936.192000] ohci1394: fw-host0: SelfID is inconsistent [0x82f4817f/0x097f08c2]
[17179936.192000] ohci1394: fw-host0: SelfID is inconsistent [0x7ec27e80/0xf780f73d]
[17179936.192000] ieee1394: SelfIDs failed root check
[17179936.192000] ieee1394: Error in SelfID stage, resetting
[17179936.192000] ohci1394: fw-host0: SelfID is inconsistent [0x81e3817f/0x087f08c0]
[17179936.192000] ohci1394: fw-host0: SelfID is inconsistent [0x7e807e80/0xf700f73f]
[17179936.192000] ieee1394: SelfIDs failed root check
.....
Stopping out-of-control reset loop

What to do???
Kjell

---

