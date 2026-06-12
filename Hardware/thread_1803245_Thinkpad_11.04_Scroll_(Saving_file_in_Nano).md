---
title: "Thinkpad 11.04 Scroll (Saving file in Nano)"
date: 2011-07-13
forum: Hardware
---

### Post by pyro226 on 2011-07-13
I'm in Ubuntu 11.04 and am trying to get the middle trackpoint button to scroll when I hold the button.  I'm trying to follow the instructions from [http://www.eastwoodzhao.com/thinkpad-middle-button-scroll-ubuntu-linux/](http://www.eastwoodzhao.com/thinkpad-middle-button-scroll-ubuntu-linux/) 

When I try to exit and save from nano, I get the error "[Error writing /usr/lib/X11/xorg.conf.d/20-thinkpad.conf: No such file or dir]"

How do I save or make the file?

---

### Post by tyraen on 2011-07-15
Do you have permission to save there? It could also be that the directory tree is missing a folder somewhere along the way.

It's likely that /usr/lib/X11 exists, but maybe you're missing xorg.conf.d. Try creating that directory as root.

EDIT: Actually, the path has changed as of 10.10: /usr/share/X11/xorg-conf.d/20-thinkpad.conf

---

