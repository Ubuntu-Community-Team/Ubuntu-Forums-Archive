---
title: "Remaining wacom problems in Edgy"
date: 2006-11-07
forum: Hardware &amp; Laptops
---

### Post by Curtisc on 2006-11-07
I've got my wacom (graphire 2) tablet just about working.  The two remaining problems are:
1) The scroll wheel is inverted.  I searched, and this seems to be a common problem with no evident solution.  Anyone get it to work?
2) I'd like to make the mouse move faster.  In Breezy, I could add "Option" "Speed" to the xorg.conf, but this stopped working in Dapper and up.  Now, any "Speed" option (even 1.1) makes the mouse acceleration unusably fast.  Is there another way to change the way the mouse moves?

---

### Post by deepwave on 2006-11-07
Could you post your xorg.conf, especially the sections for the Wacom devices?

I found that Option Mode "Relative" solved most of my problems.  Never really had a too fast cursor issue.  Then again I have Wacom Graphire 4 not a Graphire 2 tablet.

---

### Post by Curtisc on 2006-11-07
Here's the cursor part of my xorg.  The stylus and eraser work properly in the GIMP, so I don't think I want to mess with them.  I also tried changing the "ZAxisMapping" parameters, but I couldn't get scrolling to work.  The cursor right now is too slow, it's only when I add the "Option" "Speed" [some number] that it gets way too fast.  Thanks for the help.

```
Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
 Option        "Mode"          "relative"
# Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection
```

---

### Post by gamx on 2006-11-27
I have the same problem. Everything works except the wheel. It moves backwards...

---

### Post by nigeltao on 2006-12-26
I filed a bug.
[https://launchpad.net/distros/ubuntu/+source/wacom-tools/+bug/77226](https://launchpad.net/distros/ubuntu/+source/wacom-tools/+bug/77226)

---

