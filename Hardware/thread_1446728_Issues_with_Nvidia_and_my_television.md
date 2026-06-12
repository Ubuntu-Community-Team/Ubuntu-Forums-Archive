---
title: "Issues with Nvidia and my television"
date: 2010-04-04
forum: Hardware
---

### Post by fuzuoko on 2010-04-04
I just upgraded my computer the other day, and i've been able to get everything working... except my television. It was working fine before (so i know it can handle the resoloutions i'm trying for). Anyhow, i'm using a GeForce 6150, and the 185 nvidia driver. 

Every time i try to specify a mode in my xorg.conf, it gets rejected by the driver. 

(WW) NVIDIA(0): No valid modes for "1920x1080"; removing.

I added my modeline to the monitor section of xorg.conf, then added it to the screen section (hoping to force it) and still the same. 

After getting extremely frustrated, i decided to try and use the IgnoreEDID function of the driver. This failed miserably and wouldn't boot. 

I've searched all over, and nothing has helped. Anyone have any suggestions? I'm sick to death of having 1024x768 on a 16:9 display....

---

### Post by fuzuoko on 2010-04-05
Bump

---

### Post by Dugger5688 on 2010-04-05
What TV are you using, and what cable (VGA, DVI, HDMI) are you using?

---

### Post by cchhrriiss121212 on 2010-04-05
You should be able to set resolution with nvidia-settings.
185 is quite outdated if you want good video performance (I assume you do with a TV display). Have a look at this for new drivers:
[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

---

