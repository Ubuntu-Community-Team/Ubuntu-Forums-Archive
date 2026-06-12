---
title: "Freaking out after upgrading!!!"
date: 2009-05-09
forum: Installation &amp; Upgrades
---

### Post by 0per4t0r on 2009-05-09
I just upgraded from 8.10 to 9.04, and it started up in low-graphics mode for some reason, and now it's not running any x servers or something! I was an idiot, and i didn't get rid of outdated software packages before restarting, and I was thinking about using computer janitor to fix it. Do you have any advice?

---

### Post by cariboo on 2009-05-09
Depending on what video card you have, just remove all the drivers using synaptic package manager, then restart in recovery mode and use 

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

to create a default /etc/X11/xorg.conf, then type exit to continue on to your desktop where you should be able to install the proper drivers.

---

### Post by pbpersson on 2009-05-09
> **0per4t0r said:**
>  I was thinking about using computer janitor to fix it. Do you have any advice?

I have heard that computer janitor goes a little crazy and starts throwing out stuff you really need.

---

### Post by 0per4t0r on 2009-05-09
> **pbpersson said:**
> I have heard that computer janitor goes a little crazy and starts throwing out stuff you really need.
Can anyone verify this?

---

### Post by gaj1967 on 2009-05-09
> **0per4t0r said:**
> I just upgraded from 8.10 to 9.04, and it started up in low-graphics mode for some reason, and now it's not running any x servers or something! I was an idiot, and i didn't get rid of outdated software packages before restarting, and I was thinking about using computer janitor to fix it. Do you have any advice?

What kind of card are you using? I have a Nvidia and it went into low res also. The thread linked below helped me out.

[http://ubuntuforums.org/showthread.php?t=1146835](http://ubuntuforums.org/showthread.php?t=1146835)

Gil

---

### Post by 0per4t0r on 2009-05-12
Okay, [[COLOR=#D40000]**cariboo907**[/COLOR]]("http://ubuntuforums.org/member.php?u=77104")'s advice worked fine, but now, after i installed all the packages for the nvidia drivers version 180, it won't show up in restricted drivers!! All I see is one simply called "nvidia," and nothing else, and I can't enable desktop effects or compiz.

---

### Post by 0per4t0r on 2009-05-12
Okay, problem solved.

---

