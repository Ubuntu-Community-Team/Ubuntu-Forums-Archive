---
title: "Vostro V13 - Synaptic touch pad issues - Please HELP!! Maverick"
date: 2010-10-12
forum: Hardware
---

### Post by benjio123 on 2010-10-12
I've searched the forum and support site extensively and have found no  fix, although it seems to be affecting other dell laptops as well...
The problem is that the touchpad is recognised as a "PS/2 Generic Mouse"  instead. I therefore have no scrolling at all, no multitouch/gestures,  no control of speed, or anything touchpad related.

All of the info I've found is for older versions that primarily consist  of someone recommending to edit the xorg.conf file, then the OP replying  that it didn't work. I'm on 10.10 and can't even find the xorg.conf  file (although I'm a bit of a noob and it's not in the usual place). 

It doesn't work when booting from the liveCD, or installing, both 32 and 64 bit.

My laptop didn't come with ubuntu installed, so I can't get support from  dell, but they do sell this model with ubuntu. There HAS to be a way to  fix this. The hardware is certified for 10.4 64-bit, but I had the same  problem on that too.
[http://webapps.ubuntu.com/certificat...e/201004-5578/]("http://webapps.ubuntu.com/certification/hardware/201004-5578/")

Any help is much appreciated!!

Edit: Output of my xinput list
xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                          id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; HID 413c:8161                               id=10    [slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_1.3M               id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]

---

### Post by xshadow on 2011-02-11
Please read this bugreport for solution.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/380126](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/380126)

---

