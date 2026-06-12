---
title: "No desktop effects with ati x1600..."
date: 2009-08-03
forum: Hardware
---

### Post by szczym on 2009-08-03
helo all 

I run jaunty on imac 4.1 with ati x1600. After fresh install, compiz was working but 3d been hanging my desktop so i downgraded to Xorg 1.5.2 for fglrx. 3d was working but i head flickering effect so i kicked out fglrx, upgraded all back to normal, reinstalled xserver-xorg-* and after few hours head all back working. Yesterday.

But today after rebooting i dont have desktop effects and moves play with flickering effect...

Currently i have updated drivers from here:
[https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates)
It was not working also with ones from official repository 

Any idea what could i do to have dekstop effects back working like yesterday? Various modifications to xorg.conf dont seem to change anything ...

---

### Post by szczym on 2009-08-03
ok, i get it working at least :guitar:

i compiled drivers via info from here:
[http://onlyubuntu.blogspot.com/2009/05/howto-enable-ati-unsupported-cards-in.html](http://onlyubuntu.blogspot.com/2009/05/howto-enable-ati-unsupported-cards-in.html)

and after restarting gdm screen was black like a Siberian night in November so i drunk more mate and did:

sudo apt-get install --reinstall xserver-xorg-video-*

And on next boot it worked. strange, before i been doing it did not helped.
dont know what about next reboot ...

---

