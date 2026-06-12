---
title: "Epson v370 scanner and VueScan on Ubuntu 21.04"
date: 2021-08-24
forum: Hardware
---

### Post by andro-bernard on 2021-08-24
Does anybody have the combination in the subject line working in Ubuntu 21.04?

VueScan does not recognize the scanner although it is seen on the system as seen by lsusb, I have been through all the rigmarole of installing the epsonscan2 drivers from Epson, with no success. Hamrick software has not eplied to our support request, which I find rather strange - possibly not a good sign.

I am aware of a dozen things to with iscan and so on, but almost everything I find refers to the epkowa driver, which is obsolete I assume, as it is nowhere to be found, and many of the Epson pages lead to 404 errors or blank.

In short, the gist of this question is: am I flogging a dead horse? Is this scanner just simply an Epson that is not supported? I'd appreciate hearing from anybody who has this working, specifically with Ubuntu 21.04. I might add that we have exactly the same problem with Debian 11, for what it's worth. The scanner is not all that old, so I find these difficulties surprising.

---

### Post by brian_p on 2021-08-24
A long shot. Give ```
lsusb -v | grep -A 3 bInterfaceClass.*7
```

---

### Post by rbmorse on 2021-08-24
Contact Hamrick.  Last time I had a problem like this they were very responsive and came up with a solution in short order (i.e., instructions even I could follow.  Problem turned out to be user error, but they were very nice about it).

---

