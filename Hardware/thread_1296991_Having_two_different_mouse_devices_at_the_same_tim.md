---
title: "Having two different mouse devices at the same time"
date: 2009-10-21
forum: Hardware
---

### Post by BASICman on 2009-10-21
On my desktop, I've got an IBM model M keyboard with a trackpoint built into it (attached via the PS2 mouse port).  I also have a wireless USB mouse.  My problem is that the mouse settings required for each are different.

Basically, if I set up my mouse speed and sensitivity so that the trackpoint work properly, then my USB mouse is too fast.  If I set it up for the USB mouse, the trackpoint is so slow as to be unusable.  I was wondering if there was some way to set up my mouse settings such that a different speed/sensitivity would be used by the PS2 mouse (trackpoint) and the USB mouse.

---

### Post by Dark_Stang on 2009-10-21
Dumb question... why not just have 1 mouse?

---

### Post by Lars Noodén on 2009-10-21
That's a good question.  The solution may involve messing with a copy of /etc/X11/xorg.conf, though.  Out of the box, ubuntu treats all mice the same and as a single mouse.  You might get some hints from multi-seat, and just do the part for the mice:

[http://blog.chris.tylers.info/index.php?/categories/6-X-Window-System-X11](http://blog.chris.tylers.info/index.php?/categories/6-X-Window-System-X11)

Myself, if I would want that if I plug in two mice I would get two pointers on the screen.

---

### Post by BASICman on 2009-10-21
What I don't get is that it works fine on my Thinkpad.  I have a dock with a USB mouse, and I use the trackpoint when undocked.  The mouse speed is fine for both the trackpoint and the USB mouse.

As for why the two pointing devices:  trackpoint is useful for coding or writing, when I don't want to take my hands off the home row.  But the mouse is essential for Photoshop.

---

### Post by BASICman on 2009-10-26
[bump]

Still having no luck with getting the two pointing devices to work optimally.  What I want to know is whether or not theres a way that Gnome can say "Hey, he has two pointing devices!  Maybe I should let him set different speeds for each."

---

### Post by diesch on 2009-10-26
[https://wiki.ubuntu.com/X/Config/Input](https://wiki.ubuntu.com/X/Config/Input) may help

---

### Post by ZICODIAN on 2011-05-10
You might consider using xset:

[http://manpages.ubuntu.com/manpages/intrepid/man1/xset.1.html](http://manpages.ubuntu.com/manpages/intrepid/man1/xset.1.html)

You could set up two shell scripts, one script for each device, containing a command such as the following:

```

#!/bin/bash

xset m 6 2

```

Change the settings in accordance with your preferences.

Run the appropriate script for the device you wish to use.

---

