---
title: "XKB config error (MB5.1 - Karmic)"
date: 2010-02-01
forum: Hardware
---

### Post by P!g on 2010-02-01
Hey all,

I have been really enjoying Ubuntu 9.10 on my MB5.1 for the past 2 weeks. I've got everything working using the basic assist page at [https://help.ubuntu.com/community/MacBook5-1/Karmic](https://help.ubuntu.com/community/MacBook5-1/Karmic) but i've been having quite a bit of trouble finding someone who has had this same problem i'm having. 

I want to make my super key the same as my ctrl so i can cmd+v, +w, +q, +c, etc... i followed the info posted at:
[https://help.ubuntu.com/community/MacBook5-1/Karmic#Keyboard%20functions](https://help.ubuntu.com/community/MacBook5-1/Karmic#Keyboard%20functions)
[http://ubuntuforums.org/showthread.php?t=217580](http://ubuntuforums.org/showthread.php?t=217580)
and
[http://www.linuxquestions.org/questions/linux-software-2/error-activating-xkb-configuration-probably-internal-x-server-problem.-184652/](http://www.linuxquestions.org/questions/linux-software-2/error-activating-xkb-configuration-probably-internal-x-server-problem.-184652/)

but none of them work. 

_**Here's the error message:**_
Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10604000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd


any advice is greatly appreciated... :D


-also i figure since it's my first post i'd just say thanks to all those who have busted *** so that i can have a great operating system.

---

