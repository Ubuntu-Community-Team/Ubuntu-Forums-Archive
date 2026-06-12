---
title: "screen brightness"
date: 2008-10-04
forum: Hardware
---

### Post by psaikido on 2008-10-04
On a Fujitsu Siemens Amilo laptop I have Hardy Heron installed.  All good except that the screen brightness is very low.  After much trawling around I have found a fix which is:
ctrl+alt+f1 to a virtual console, log in then:
sudo vbetools post

..back to the desktop with alt+f7 and the screen brightness is back up to a useable level.

I put this here for others to benefit from maybe and also to ask if there is a permanent fix possible for this.  Does anyone know why this happens and if there are plans to improve?

--
psaikido

---

