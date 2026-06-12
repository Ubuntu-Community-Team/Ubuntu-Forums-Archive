---
title: "switched out nvidia card, now black screen with restricted drivers"
date: 2008-05-18
forum: Hardware
---

### Post by slamgauge on 2008-05-18
I recently took my nvidia 8600gt out of my 8.04 production(work) machine and put it into a new media center box that I built.  I put an slightly older 6600gt in the work box and reconfigured xorg.  The card works fine until I try to turn on the restricted drivers,  after the startup splash screen it goes black.  

I have tried reinstalling the nvidia restricted drivers and using envy to see if maybe it would catch something that I am missing, all to no avail.  Anybody have any suggestions as to what I should try next?

---

### Post by EXCiD3 on 2008-05-18
Try this in terminal to reconfigure your xorg, then try envy or restircted drivers again

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by slamgauge on 2008-05-18
Nope, same thing as before.  Right after the splash, black screen.  I cant even get to a terminal.

---

