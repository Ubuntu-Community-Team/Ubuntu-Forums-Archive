---
title: "Internal card reader is detected but won't r/w"
date: 2010-11-27
forum: Hardware
---

### Post by halcyonz on 2010-11-27
Just added an internal 4-1 Flash media reader to my computer via a motherboard connection. Ubuntu (10.10 on HP m7350n) recognizes the device but it refuses to recognize the media inserted. The media in question is a Sandisk 4GB class 4 SDHC card. I purchased two and neither are detected.

This is what dmesg has to say...

> dmesg | tail```
[  170.960031] usb 4-1: reset full speed USB device using uhci_hcd and address 2
[  181.224022] usb 4-1: reset full speed USB device using uhci_hcd and address 2
[  197.492019] usb 4-1: reset full speed USB device using uhci_hcd and address 2
[  197.760017] usb 4-1: reset full speed USB device using uhci_hcd and address 2
[  208.024019] usb 4-1: reset full speed USB device using uhci_hcd and address 2
[  208.178082] sd 6:0:0:0: Device offlined - not ready after error recovery

```Willing to give anything a try, I have tried some basic things such as restarting without reader attached then plugging in and other power cycling options but to no avail. Most post I have read discussing similar issues deal with a previous karmic update that seems to have been reolved in 10.10.

Thanks!

---

### Post by halcyonz on 2010-11-27
Just tried on my buddy's XP tower and the SD reader works fine. So I know its not the reader or the media, so at least I know it probably has an easy fix! Or at least a fix, heh. anyone want to give it a stab?

---

### Post by halcyonz on 2010-11-27
Update:
Whenever I restart with media in the reader it hangs at the bios screen, I thought it was because it was attempting to boot from the empty media, however my HDD is set as my first boot device. Updated my kernel and headers to the latest update which install something with apparmour that screwed with the output of dmesg | tail, so I removed every apparmour entry and its back to the output listed above. I do however plan to reinstall apparmour after I figure out this SD problem. A little help might make this easier though?

I have officially spent way too much time working on this, this is what I have so far...
*kernel bug (upgraded to latest)
*usb 2.0 problems (uhci_hcd removal suggested, but that will set everything back to usb 1.1 which is  no bueno)
*lack of power (power lines are good, checked continuity with multimeter and led turns on when media is inserted)

Anyone?

---

