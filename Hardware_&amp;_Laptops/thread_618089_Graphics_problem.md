---
title: "Graphics problem"
date: 2007-11-20
forum: Hardware &amp; Laptops
---

### Post by schreckles on 2007-11-20
I have a HP Pavilion ze5300 with a Radeon IGP 345m. I tried to change the video driver so that I could play frets of fire and supertux (both were blurred and unplayable when I tried.) Now that I've done that, everything is always blurred like frets of fire and supertux were. Is there a way to set the graphics back to what it was by default, as it's now unusable? I've tried just changing it back, despite the fact that I could barely see what I was doing, but to no avail. When I click the test button, the keep configurations/cancel screen that comes up looks fine, but when I hit apply, it goes back to just staying blurry. Can ANYONE help me? I'm dying not being able to use ubuntu on this laptop.

---

### Post by schreckles on 2007-11-20
Nevermind I've got it figured out. For anyone that runs into this problem, just reboot into recovery mode, and type in
```
sudo dpkg-reconfigure xserver-xorg
```
and go through and change your settings to whatever you think will work best. Took me a couple tries to get everything set up exactly as I want, and I still can't play frets of fire or supertux (GRRR!!!!) but it's now a usable laptop again.

---

