---
title: "Fixing after installing newest ati driver"
date: 2007-01-18
forum: Hardware &amp; Laptops
---

### Post by tehquickness on 2007-01-18
Ok, I admit I was dumb. I tried to install the new ati driver from ati. It screwed up my computer. However, I have gotten pretty close to getting back to normal however, when I login to gnome with GDM, it quits after 10 seconds and tells me to log in with gnome safe. I think there is something wrong with the /etc/gdm/PreSession/Default file that is triggering this problem. The .xsession error is as follows:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "tehquickness"
/etc/gdm/Xsession: Beginning session setup...
.: 106: Can't open /etc/profile

I appreciate your help. Hopefully we can get this solved. I think it might have something to do with line 2 of the error above.

---

