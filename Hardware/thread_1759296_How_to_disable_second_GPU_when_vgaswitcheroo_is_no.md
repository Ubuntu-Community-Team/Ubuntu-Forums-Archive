---
title: "How to disable second GPU when vgaswitcheroo is not present?"
date: 2011-05-15
forum: Hardware
---

### Post by sean.leber on 2011-05-15
Hello, I'm a n00b and this is my first post ever to the ubuntu forums.  I am having a hard time trying to disable my Radeon 4550 which chews through battery life even though I can't really use it in Ubuntu 11.04 (apparently it doesn't play nicely, and yes, I have endlessly tried to install it using the new ATI drivers and each time I try the install cuts out in the middle, I have yet to successfully complete a single install).

All of the forums use vgaswitcheroo to disable a second card, but when I tried to run

> $ ls -l /sys/kernel/debug/vgaswitcheroo/switch
ls: cannot access /sys/kernel/debug/vgaswitcheroo/switch: Permission deniedor

> $ sudo echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
bash: /sys/kernel/debug/vgaswitcheroo/switch: Permission denied
it turns out that I don't actually have a 'vgaswitcheroo' folder in /sys/kernel/debug/ however when I run the following:

> $ grep -i switcheroo /boot/config-2.6.*
CONFIG_VGA_SWITCHEROO=yI get a =y response, which leads my meager mind to believe that VGA_SWITCHEROO is either running or at least somewhere on my system.  I got these terminal commands from the following post:

[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

I'm running an HP tm2t 1100 with integrated Intel graphics and a Radeon 4550 card.  Ultimately, I'd love to use my Radeon 4550 card and ditch windows all-together, but I'm currently hanging on to my windows boot just to watch 720p and 1080p movies.   If I can't use the card I can live with it, but I'd like to be able to turn it off so it doesn't hog so much battery when I'm doing my day-to-day in ubuntu.  Any help I can get on this would be great, thanks!

---

### Post by yanqian on 2011-05-17
[http://ubuntuforums.org/showthread.php?t=1751726](http://ubuntuforums.org/showthread.php?t=1751726)

```

sudo -i
(Enter Password)
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
```

---

### Post by mstrlocke on 2011-07-26
I have the same problem as Sean.  When I try yanquian's solution, I get the following:

-bash: /sys/kernel/debug/vgaswitcheroo/switch: No such file or directory
root@Linda-HP-Linux:~#

Help?

---

