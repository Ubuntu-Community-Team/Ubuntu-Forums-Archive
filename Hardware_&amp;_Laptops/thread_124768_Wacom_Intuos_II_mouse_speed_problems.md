---
title: "Wacom Intuos II mouse speed problems"
date: 2006-02-02
forum: Hardware &amp; Laptops
---

### Post by affected on 2006-02-02
Hello,
I am running Kubuntu breezy on an AMD64 system with an nvidia card using twinview. I have just installed the linuxwacom driver, replacing the driver that comes with breezy. In a way this made the wacom mouse behave nicer, in that when I lift the mouse up and put it back down it no longer jumps at all in relative mode. However, the cursor speed is a bit too low. If I use xsetwacom to set it higher, I run into trouble: up to the default value of 6 everything is OK, just the speed is too slow, but the moment I crank the speed up to 7, it seems the horizontal speed becomes double that of the vertical speed. I'm guessing this has to do with having a dual monitor setup, but I have no idea what I could do to fix this. I have also tried adjusting the "speed" option in xorg.conf for cursor, but setting that to anything higher than "1" yields the same problem as xsetwacom.

Any ideas? I'm getting a seriously tired and sore arm here with this mouse speed.

---

