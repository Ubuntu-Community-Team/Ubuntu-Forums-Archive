---
title: "Scanner"
date: 2006-06-27
forum: Hardware &amp; Laptops
---

### Post by Milambar on 2006-06-27
Well, it looks like I'm going to have to revert to windows unless I can get answers fast :(

Im a photographer, and I need to scan in some photographs before 2pm GMT, tomorrow.

Until I upgraded to Ubuntu 6.06 from 5.10, my scanner worked flawlessly and perfectly under Ubuntu.

Now, having upgraded to 6.06, all it ever tells me is:
Failed to open device `snapscan:libusb:004:003': Invalid argument.

Is there a fix for this?

---

### Post by Milambar on 2006-06-28
I finally resolved this myself. It appears for some reason the upgrade to 6.06 removed the firmware files that SANE needs for epson scanners. I have no idea why, copyright reasons since the firmware files are actually owned by Epson?

The fix was just to uzip, and cabextract the firmware files off the install cd that came with the scanner, and copy them back.

Having done so, the scanner now works flawlessly again.

---

