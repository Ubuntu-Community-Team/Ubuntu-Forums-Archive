---
title: "Ubuntu minimal + fluxbox = slow 3D after restart"
date: 2009-12-16
forum: Hardware
---

### Post by Nostradani on 2009-12-16
Hey,

Well, I set up my system with Ubuntu minimal (console only, 9.10) to get a nice boot time. I then installed an XServer and Fluxbox:

```
sudo apt-get install xorg fluxbox mesa-utils
```

After that completed I started fluxbox ("startx") and tried glxgears which gave me over 8000 frames at 5s.

But then rebooted the system and since then I'm stuck at 900 frames at glxgears (and also very slow performance at other OpenGL applications). I also tried the normal Ubuntu installation, but there everything is fine.

Btw. I use an Radeon Moblity 9600 with the open source driver "radeon". I already compared the xorg log and the loaded kernel modules before and after the first restart. Both are identical.

So what went wrong and how to resolve it? Any ideas?:confused:

---

