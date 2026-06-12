---
title: "Netbook edition screen resolution"
date: 2010-06-07
forum: Hardware
---

### Post by Experimental on 2010-06-07
I have a notebook that has 10.04 netbook edition. It's graphics card can support widescreen resolutions but in monitors option there's only 800x600 and 640x480. My graphics card is sis 3 graphics. How can I change it's resolution to widescreen resolutions ?

---

### Post by FemmeFatale on 2010-06-07
It would be much better to mention brand/model of your netbook.

Take a look at: [http://ncc-1701a.homelinux.net/~linux-sis/](http://ncc-1701a.homelinux.net/~linux-sis/)

and make sure you have a proper driver for your hardware. Once you are done and it still doesn't work, go to xorg.conf and under the monitor configuration section, load the "sis" driver (that's the way it's called).

---

### Post by Experimental on 2010-06-08
Where's xorg.conf in lucid lynx ? oh i see etc/x11/

---

