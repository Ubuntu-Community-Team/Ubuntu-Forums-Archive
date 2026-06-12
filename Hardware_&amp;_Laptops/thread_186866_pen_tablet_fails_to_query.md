---
title: "pen tablet fails to query"
date: 2006-06-02
forum: Hardware &amp; Laptops
---

### Post by vinzer on 2006-06-02
i've just installed the xorg acecad package, and i modified my xorg.conf accordingly (device is on /dev/input/event3). but then whenever xorg starts, and i read the log, it always ends up with these lines:

(EE) Unable to query/initialize AceCad hardware.
(EE) PreInit returned NULL for "Tablet"

i can't seem to find the reason for this, since the tablet does work as a basic mouse, so i doubt that it is a problem with the connection or something.

any ideas on how to resolve this? maybe someone who experienced the same error messages but with another device and solved it would care to give some possible solutions? any help would be much appreciated. :)

---

### Post by gershon on 2006-12-31
can second that.

same xorg problem, using 1.1.0.

not recodnized as extended input... 
works "fine" as a mouse, guessing that having failed the query it does'nt take the tablet's
dimentions into account and the absolute (only, realtive does'nt work) postion is inaccurate.

[http://acecad.sourceforge.net/](http://acecad.sourceforge.net/) claims to have updated sep 2006 but the link is dead...](*,)

---

