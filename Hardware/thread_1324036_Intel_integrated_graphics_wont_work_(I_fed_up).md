---
title: "Intel integrated graphics wont work (I f***ed up)"
date: 2009-11-12
forum: Hardware
---

### Post by Softarn on 2009-11-12
So I have a T400 with two graphics cards. Were running the integrated but wanted to get the discrete ati working to. Switched graphics cards and got ati working by installing drivers from their website. Switched back again to integrated intel and had problems with getting the graphics to work, well compiz and games doesn't work. Ati had taken a backup of my xorg.conf, i thought, it was totally empty. So I ran "X -configure" and got a new one. 

When I try to run glxgears i get this output:
```
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  14
  Current serial number in output stream:  14
```

My Xorg.0.log
[http://pastebin.com/m7db376e2](http://pastebin.com/m7db376e2)

My xorg.conf
[http://pastebin.com/md056bd5](http://pastebin.com/md056bd5)

If you look at Xorg.0.log line 103-116 it seems like its trying to load some ati modules.

I've installed some new intel drivers, "xf86-video-intel".

---

