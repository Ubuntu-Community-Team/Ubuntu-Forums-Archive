---
title: "Minimal Xorg install"
date: 2009-09-10
forum: Installation &amp; Upgrades
---

### Post by executivul on 2009-09-10
Hello,
I'm trying to make a minimal Xorg install,
but "apt-get install xorg" wants 124new packages, 111Mb of additional disk space,
in the list I can find: xserver-xorg-video-mach64, video-radeon, video-s3virge,
I do not need all these.

How can I install only the required packages for my config? (onboard intel video)

Thank you

---

### Post by earthpigg on 2009-09-10
what does it give you when you do apt-get install --no-install-recommends xorg?

---

### Post by executivul on 2009-09-10
with the "--no-install-recommends" i get 114 packages, 65.5mb :)
it's better but the unneeded video drivers are still there, and there are quite a few
thank you

---

### Post by earthpigg on 2009-09-10
well... those 114 packages are what Debian has determined are the absolute minimum for X to run.

without getting really nitty gritty, i think thats about as low as you can go without risking system instability.

---

### Post by executivul on 2009-09-10
[B]Not affraid to get dirty ...

[/B][B][B]apt-get install --no-install-recommends xinit xserver-xorg-video-intel xserver-xorg-input-synaptics xserver-xorg-input-kbd xserver-xorg-input-mouse xfonts-base openbox

and openbox runs :)[/B]
[/B]

---

