---
title: "Epson scanner reporting as two devices"
date: 2012-03-08
forum: Hardware
---

### Post by EarlsFurniture on 2012-03-08
I recently installed Ubuntu 10.04 x64 (desktop) on a new Gateway system.  I was able to successfully install and use an Epson Perfection 4900 scanner.  But for some reason, when the scanner is first detected (e.g. - when starting Xsane) it sees TWO scanner devices.  One is "unknown scanner device" and the other is the correct Epson Model#.  It isn't that big of a deal, except the default device is always the "unknown" device and the user has to choose the correct model every time.  Is there a way to remove this unknown device, or a way to set the proper one as the default?  Any idea how the unknown device got there in the first place?  Thanks for any advice...

---

### Post by dandnsmith on 2012-03-09
I haven't used Sane for may years, but remember that the documentation shows how to set the default device to be used.
Have you used lspci or lshw to show device details?
Have you tried Simple Scan to see if that, also, tries to use a wrong default?

---

### Post by EarlsFurniture on 2012-05-16
Not yet, but I'll try all of those and see what happens.  I didn't seem to find info in setting the default device, but I'll look again.

Are you using something other than Sane?  I might try other options as well.

---

