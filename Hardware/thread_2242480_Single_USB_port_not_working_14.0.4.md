---
title: "Single USB port not working 14.0.4"
date: 2014-09-02
forum: Hardware
---

### Post by sauravp on 2014-09-02
Just recently upgraded to 14.0.4 after having lots of issues getting the GUI to load properly. Fixed all those issues but now my USB Port wont work.

It's a single USB port that wont recognize any device, currently trying to get my Keyboard to work (Steelseries). The power lights flash for a second when I plug it in and then from there it doesnt seem to recognize the device. The other USB port works for my mouse and keybaord when I swap it in and out.

Current UBUNTU version: 14.0.4
Device: Macbook Pro 5,5 (No OSX Installed anymore)

Any suggestions? Only thing I found was about a USB port being disabled but hwinfo is depreciated. 


Thanks.

EDIT1: Seems when I plug my phone in that USB port it charges, and shows up in the device list and I can browse devices. Only my mouse and keyboard seem to not be recognized.
EDIT2: using 'tail -f /var/log/syslog' see no changes when pluging in the Keyboard, however I DO see the changes from unplugging my Phone (Galaxy S4)

---

### Post by varunendra on 2014-09-04
Is "Legacy USB" support enabled in BIOS? Make sure it is.

---

