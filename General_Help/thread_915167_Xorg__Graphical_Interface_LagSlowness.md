---
title: "Xorg / Graphical Interface Lag/Slowness"
date: 2008-09-09
forum: General Help
---

### Post by Joe_CoT on 2008-09-09
Every couple of days, out of nowhere, Xorg seems to screech to a halt. It takes forever for windows to redraw, minimize, close, etc. Looking at top, Xorg is using some 70% of the cpu, for no apparent reason. If I log out and log back in (ie restart xwindow), the problem is gone.

I see nothing weird in my dmesg. Is this something other people have run into? Anything I should look for?

---

### Post by Joe_CoT on 2008-09-11
I'd really appreciate some help with this. A coworker suggested I do an strace of Xorg when this happens, which is below, but I don't really know what I'm looking for. I'm not even sure it's Xorg's fault.

[http://joeterranova.net/code/xorg.strace.txt](http://joeterranova.net/code/xorg.strace.txt)

---

### Post by Joe_CoT on 2008-09-12
Seems to have been a problem with the nvidia driver. I switched to the open source nv driver, and not only did it solve this problem, but also another problem where my screens would come up to jibberish (snowing on the screen), and the machine would lock up. Maybe I'll try updating the driver later.

---

