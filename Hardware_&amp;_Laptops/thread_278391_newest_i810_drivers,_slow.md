---
title: "newest i810 drivers, slow"
date: 2006-10-16
forum: Hardware &amp; Laptops
---

### Post by terrax on 2006-10-16
Hello ubuntuforum.

I have just installed aiglx with the newest i810 drivers from this repository:

deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) dapper main aiglx

My original i810 driver-version was: 1:1.4.1.3-0ubuntu6
Everything worked alright with that driver. The only thing, which didn't, was some opengl programs and the screensavers. (It is mentioned many places). The only thing, which doesn't work with this driver, is beryl. Everything is upside down. Looks crazy.

When I installed the version 1:1.6.5-0ubuntu1
The screensavers etc. worked, but with a huge framedrop. I got the half points with glxgears, but eventually glxgears will crash. And a lot of other 3d apps will crash.


Anyone know how to install a newer i810 driver? og any solution?

---

### Post by dtfinch on 2006-10-16
What does glxinfo say about "Direct rendering"? What does your /etc/X11/xorg.conf look like? And is the resolution at the login screen the same as it is after you log in?

---

### Post by terrax on 2006-10-17
This is exactly the problem I got. 

[HTML]
https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-i810/+bug/61306
[/HTML]
Its a bug in the driver. But I wonder when there will be a new package avalible? Or if any could make a new package of the cvs?

For Dapper xorg 7,0.

---

