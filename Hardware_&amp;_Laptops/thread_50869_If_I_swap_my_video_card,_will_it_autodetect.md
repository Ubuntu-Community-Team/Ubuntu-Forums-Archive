---
title: "If I swap my video card, will it autodetect?"
date: 2005-07-21
forum: Hardware &amp; Laptops
---

### Post by qwert231 on 2005-07-21
My video card is getting flakey. I just installed Ubuntu 5.04. If I swap out my video card, will it choke? Or will it autodetect?

---

### Post by az on 2005-07-21
You will have to reconfigure the xserver.

Boot into recovery mode.
dpkg-reconfigure xserver-xorg
answer the questions (take the default)
init 2


you are done.

---

