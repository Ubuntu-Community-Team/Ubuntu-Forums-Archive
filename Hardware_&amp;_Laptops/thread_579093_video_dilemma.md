---
title: "video dilemma"
date: 2007-10-17
forum: Hardware &amp; Laptops
---

### Post by dbcoolio on 2007-10-17
I just upgraded to Gutsy on my laptop, and the video driver it initially picked was sort of buggy, so I tried to change drivers, and things got sort of weird, so I switched it back to what it was, but now it is doing something strange.
During the process, the resolution got downgraded from 1280x800 to 640x480, and so it also changed that setting for the root user (I'm guessing) so the log-in screen is coming in at 640x480, and then after it logs in the top left most 640x480 pixels show, and the rest are orange like the root background. However, If I log in using the "gnome-failsafe" session option, everything works fine.

there's got to be some easy fix for this, I'm just not sure what it is.

---

### Post by dbcoolio on 2007-10-19
I was able to fix it with:
```
sudo dpkg-reconfigure xserver-xorg
```

---

