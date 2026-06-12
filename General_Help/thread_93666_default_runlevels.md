---
title: "default runlevels"
date: 2005-11-22
forum: General Help
---

### Post by houseofmore on 2005-11-22
Hello,

I've mucked up my runlevels while trying to tweak my bootup (speed).  Now my touchpand scroll and auto wifi doesn't work.

Is there, or can anyone provide a list of the default runlevels for services that ubuntu installs with (breezy).  Everything worked great, till I started poking around!

---

### Post by houseofmore on 2005-11-22
Perhaps someone with a pretty default install could send me a screenshoot of their sysv-rc-conf (if you have it).

---

### Post by cgirda on 2005-11-22
I would say retain your work and get the missing pieces work

 For your auto wireless do
 # echo "auto wlan0" >> /etc/network/interfaces

 For your touchpad check your xorg.conf

---

