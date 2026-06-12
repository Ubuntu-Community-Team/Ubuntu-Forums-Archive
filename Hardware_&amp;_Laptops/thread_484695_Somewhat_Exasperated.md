---
title: "Somewhat Exasperated"
date: 2007-06-26
forum: Hardware &amp; Laptops
---

### Post by pablo88 on 2007-06-26
h

---

### Post by PaulFr on 2007-06-26
Hi Pablo,

1. For your display resolution problem, you have an Intel 915 graphics controller, so the ATI / NVidia drivers will not work. One convenient way to fix it is to look at this blog post: **[http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html](http://roland-lopez.blogspot.com/2007/03/auto915resolution-ubuntu-resolution-fix.html)** which is linked to from **[https://help.ubuntu.com/community/i915Driver](https://help.ubuntu.com/community/i915Driver)**.

2. For your font problem, take a look at the "Manually" section of **[https://help.ubuntu.com/community/FontInstallHowto](https://help.ubuntu.com/community/FontInstallHowto)**.

3. For your sound recording problem, I am on shakier grounds - but a simple suggestion: did you try running **alsamixer -V capture** in a terminal ? This will show you the levels of the audio capture devices (use left and right arrows to move between capture devices, Tab to show playback/all devices). You may need to adjust the levels of the capture devices. More sources of audio problems and how to fix can be found at: **[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)**.

Hope these help.

---

