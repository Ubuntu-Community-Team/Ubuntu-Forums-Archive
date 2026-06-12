---
title: "VNC keyboard broken after 9.04 upgrade"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by oldtappan on 2009-04-27
I posted this in "[Networking & Wireless]("http://ubuntuforums.org/showthread.php?p=7154638#post7154638")" but didn't get any solutions.  Hoping this forum is better:

This was working before I upgraded to 9.04. Now when I use TightVNC 1.3.10 from Windows to my Ubuntu box, the wrong characters are getting inputted. For example when I type a space, 7 appears, s => b, d => f. Somehow my keyboard interpretation is screwed up.

My keyboard works fine on my Windows laptop and when I SSH into Ubuntu. It only seems screwed up when I use VNC. And this happened right after I did my upgrade.

Help....

---

### Post by fausto@6comm.net on 2009-04-27
same problem in a clean 9.04 installation // hopefully somebody find a solution soon

---

### Post by fausto@6comm.net on 2009-04-27
I found a solution at the end of this thread .. uuff!!!
[https://bugs.launchpad.net/baltix/+source/tightvnc/+bug/112955](https://bugs.launchpad.net/baltix/+source/tightvnc/+bug/112955)

just like this:
Just got that fixed by adding 'export XKL_XMODMAP_DISABLE=1' in $HOME/.vnc/xstartup before the last line /etc/X11/Xsession

---

### Post by oldtappan on 2009-04-27
It worked.  Thank you!

---

