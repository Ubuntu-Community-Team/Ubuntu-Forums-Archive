---
title: "scanner no longer works in jaunty"
date: 2009-05-08
forum: Hardware
---

### Post by ZeldaFan on 2009-05-08
I have an HP All in One officejet series 5510 with a scanner that used to function out of the box with xsane in previous versions of ubuntu. However, with jaunty, I get an error stating "Failed to open device 'hpaio:/usb/officejet_5500_series?serial=MY472G21M596': Error during device I/O."

Any help to get my scanner up and running again would be greatly appreciated.

---

### Post by chudder on 2009-05-08
I'm having the same problem,

I get an error that says:

"Failed to open device: 'v4l:/dev/video0': Invalid Argument

It looks like for some reason it's trying to turn on a webcam or some other type of camera

---

### Post by ZeldaFan on 2009-05-09
I'm not completely sure what I did (because I don't think I did anything), but xsane is now working for me. If any of following does help though, you can try it (even though I doubt it will help):
1. I added the "scanner" group to my User group, as it did not exist prior. However, before launching xsane again, I deleted the group. 
2. I used alt +F2 to launch xsane and it worked.

I doubt any of this will help and I still can't figure out what exactly caused it work on my system.

---

### Post by jws957 on 2009-11-14
I was running jaunty and had the same problem with an hp Officejet 6500.  I could get the scanner to work by loading the hpoj libs in Synaptic, but that didn't have support for the printer.  I just upgraded to 9.10 and both printer and scanning functions now work.

---

