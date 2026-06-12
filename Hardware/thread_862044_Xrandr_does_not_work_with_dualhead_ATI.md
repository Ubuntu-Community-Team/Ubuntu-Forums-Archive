---
title: "Xrandr does not work with dualhead ATI"
date: 2008-07-17
forum: Hardware
---

### Post by elfstone2 on 2008-07-17
Hello,
i finally managed to get a working dualhead setup with ATI, but now xrandr wont work any more.. thats quite anoying, since i want to connect my video projector and my TFT to my laptop, and both have different resolutions.

I have Kubunt 8.04. 

```

$ xrandr
Xlib:  extension "RANDR" missing on display ":0.0".
RandR extension missing

```

Any Ideas? Thx for the help.

Hm.. i cant upload xorg.conf an Xorg.0.log to the forum, so here they are:
[http://www.aojb.de/xorg.conf]("http://www.aojb.de/xorg.conf")
[http://www.aojb.de/Xorg.0.log]("http://www.aojb.de/Xorg.0.log")

---

### Post by himikeb on 2008-10-15
Is it possible your "Virtual" setting is not large enough?
Can you provide more detail, like "it only works in clone-only" mode?
The Virtual option specifies the size of the combined area - eg: I have a 1280x1024 VGA monitor and 1028x768 laptop, so my Virtual line is:
  Virtual 2304 1024
2304=1280+1024 - max width, and max height is 1024.

Good Luck.

---

### Post by elfstone2 on 2008-10-15
Thx for replying... but the problem has already been understood in the meantime. ATI driver and xrandr dont work together, ATI hat its own replacement for xrandr. Unfortunatly, that replacement cant change resolution on the fly.. so, im back to the radeon driver, and will buy an nvidia next time.

---

