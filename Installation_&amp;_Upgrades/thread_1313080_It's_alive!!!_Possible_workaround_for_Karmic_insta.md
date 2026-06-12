---
title: "It's alive!!! Possible workaround for Karmic installer problem with SATA drives?"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by Ginsu543 on 2009-11-03
After much headache and tinkering, I finally got Karmic to install on my rig. For some background, until now I had not been able to install Karmic because the installer would not recognize my two WD Raptors as separate drives but only as members of a non-existent RAID array (the two drives had been used before in a RAID array, however). I might have found a workaround that may work with others with the same problem:

1) I physically disconnected all other drives except the one I was installing to
2) I turned off "Boot Other Device" in BIOS under "Advanced BIOS Features"
3) I ran Karmic off the live CD and ran "sudo apt-get remove dmraid" in Terminal
4) I ran the installer by double-clicking on the icon

I had no success with the previous steps until I did #2, and I think that might have done the trick. If you have had similar problems and have a similar option in your BIOS, you might give turning it off a try.

---

### Post by Stewart Bunce on 2009-11-03
Tried the above and whilst it did allow me to finally see the seperate drives I could not format them (GParted claimed they were in use). After some searching I found the following page:- 

[http://osdir.com/ml/linux.kernel.device-mapper.devel/2007-04/msg00014.html](http://osdir.com/ml/linux.kernel.device-mapper.devel/2007-04/msg00014.html)

It doesn't describe exactly this issue but I suspect the underlying problem is the same - the drives have previouly been part of a fakeraid array and some of the information on this is still present. Having followed the instructions above I can now both see and format both drives.

Unfortunately the installer is now failing because of I/O errors when copying install file but i'm sure I'll get there eventually...

---

