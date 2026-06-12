---
title: "why no ATI proprietary driver in &quot;Hardware Drivers&quot;"
date: 2008-10-29
forum: Hardware
---

### Post by baosheng on 2008-10-29
Hi,

i am using Ubuntu 8.10 RC. But I can't find the ATI proprietary driver in "Hardware Drivers". Can someone tell me why? I really wanna enable Compiz on my desktop.

---

### Post by Izek on 2008-10-29
Install it from Synaptics, xorg-driver-fglrx. I had to do this too. But it WILL cause lagging.

Also, the Catalyst 8.10 (from the ati website) and below do not support the new linux kernel / xorg server, I've tried running the run files myself.

---

### Post by yaknowwat on 2008-10-29
Trust me you do not want to enable the driver.  What you'll end up with is a full terminal because X will not start.

We're stuck until ATI actually releases a final semi-stable fglrx driver that supports Xserver 1.5 .

Yes I have an integrated Xpress 1200 and I miss compiz too but thats how it is with ATI they have slow semi-unstable development cycle with linux.

Nvidia on the other hand I've seen nothing but positive even though they aren't open source they do keep up to date.

---

### Post by Izek on 2008-10-29
Then how do we remove the driver once we do have it installed? Properly, of course, since uninstalling the xorg-driver-fglrx from Synaptics will cause ubuntu to start in low-color mode without the right resolutions (for me.)

---

