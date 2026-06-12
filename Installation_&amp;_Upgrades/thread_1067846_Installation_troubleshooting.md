---
title: "Installation troubleshooting"
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by deviant937 on 2009-02-12
I recently installed Ubuntu 8.10 Desktop onto my machine. It successfully gets to the login screen and allows me to login, but then a tan background comes up and the machine hangs. The only successful of the login menu choices is the Failsafe Terminal. 

I have checked my DVD for defects and it comes back clean.

Any assistance with where to begin troubleshooting this problem would be awesome

Thanks
Solo

---

### Post by lemming465 on 2009-02-14
What's your video chip?  A good thing to try would be:

Ctrl-Alt-F1 to switch to a text console
Log in.
Then:
```

sudo -i
apt-get update
apt-get upgrade
dpkg-reconfigure xserver-xorg

```
If it's a brand new 8.10 install, there were a lot of teething problems with some ATI, some Nvidia, and some Intel video chips.  Subsequent updates have fixed most of them.  Turning off Compiz effects (System->Preferences->Appearance, visual effects tab, radio button "none") has helped a lot of people.

---

