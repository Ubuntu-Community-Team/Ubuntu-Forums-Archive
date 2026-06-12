---
title: "Firefox Page Corruption"
date: 2008-09-13
forum: General Help
---

### Post by mdramige on 2008-09-13
Up until today, this problem has been limited to [http://wiki.debian.org](http://wiki.debian.org), but I discovered another site with this same problem and I'm sure there are many more ([http://www.bloglines.com](http://www.bloglines.com)).

I'm using Firefox 3.0.1 on Ubuntu 8.04 (all packages updated) with nvidia-glx-new (169.12). This problem occurs with and without Compiz enabled.

If the screenshot doesn't explain what's going on, basically going to wiki.debian.org doesn't show that site. I have to either scroll up and down to get those sections to show or use the mouse cursor to get links to show up. I'm not even sure how to define this problem, so maybe a better Google or Ubuntu Forums search term would help. The only thing I can think of is "page corruption" but that hasn't helped so far.

Basically if you haven't experienced this, I need a better description of what is happening. What makes those sites different from others? Do you think this is a Firefox, Nvidia, or X.org issue? I'm betting on the Nvidia driver.

---

### Post by DrMelon on 2008-09-13
I see what you mean. Page elements seem to start out invisible, but when you mouse over them, or scroll they become visible. I can't seem to determine the cause; does this happen with other browsers?

---

### Post by mdramige on 2008-09-13
The two sites mentioned work fine in Galeon, but not in Epiphany. Same results in Epiphany as Firefox.

---

### Post by mdramige on 2008-09-13
I tried a few more things. I noticed that those sites contained a lot of javascript so I used noscript to disable, but that didn't help.

Debian Wiki uses MoinMoin so I checked other MoinMoin powered sites, but they all seem to work fine. 

Turning off the stylesheet makes them display fine, but that's not really an option. I just want to find out what's causing this.

Next I may revert back to the nv driver or try a new Nvidia beta driver to eliminate the graphics card.

---

