---
title: "Scanner just cycling through USB device #s"
date: 2007-04-25
forum: Hardware &amp; Laptops
---

### Post by tomgarvin on 2007-04-25
I upgraded to Feisty three days ago, but I've only just noticed this problem.  Based on the other USB problems I've seen posted, I am suspicious of Feisty.

My configuration:
 - Ubuntu Feisty (up-to-date)
 - Avision scanner
 - model AV220C2

What's happening:
Plug in and turn on scanner.  It visually reconfigs and obtains a USB device ID.  This is reflected in 'lsusb':

           Bus 005 Device 087: ID 0638:0a2a Avision, Inc.

Then the lights blink on the scanner, and on the next 'lsusb', the scanner has disappeared.  Then the lights blink again, and 'lsusb' says:

           Bus 005 Device 088: ID 0638:0a2a Avision, Inc.

You can see that it's obtained the next available USB device ID.

If I leave the scanner on and plugged in, it just does that over and over and over.  It hits 127, then starts again from 001.

I plugged in an identical scanner and it did the exact same thing.  I plugged in an Avision AV8300 scanner and it seemed to work fine.  I tried a more beefy USB cable, and that didn't help.  I did the same test on two other Ubuntu systems, one Feisty and one Edgy... same result on Feisty, but Edgy works fine (holds it's device ID).

Any insight would be greatly appreciated.

---

### Post by tomgarvin on 2007-04-26
Looks like there are a fair number of issues with USB in feisty.  I've tried disabling USB2.0 in Linux, but that did nothing.

Anyone have thoughts?

---

### Post by tomgarvin on 2007-05-15
bump

---

