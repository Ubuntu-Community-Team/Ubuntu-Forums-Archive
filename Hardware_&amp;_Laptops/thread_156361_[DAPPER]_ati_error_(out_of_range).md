---
title: "[DAPPER] ati error (out of range)"
date: 2006-04-06
forum: Hardware &amp; Laptops
---

### Post by clapton on 2006-04-06
I've been intalled ati drivers from ati binaries (web site)
And, when I start X, my monitor goes out of range.
SO, I've try to use the standard drivers and the situation is the same, so when I install driver, my monitor goes "out of range".

I' ve got an Ati radeon 9550 256 mb made by Asus.

I follow this 2 guides to help me to install,I follow the steps:
[http://www.ubuntuforums.org/showthread.php?t=148351](http://www.ubuntuforums.org/showthread.php?t=148351)
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

I know, that I can use
```

sudo dpkg-reconfigure xserver-xorg

```

But, this won't solve my problem, i'll stay withou't 3D accelaration anyway
Someone can Help?

---

### Post by mlomker on 2006-04-07
You'll want to look through /var/log/Xorg.0.log and figure out what resolution the driver is trying to configure your monitor for.  Normally the driver communicates with your monitor and figures out what the highest refresh rate is supported by both the driver and monitor and then uses it.  This may be a case where they aren't 'talking' to each other properly.

If that is the situation then you could try setting a modeline for the specific settings that your monitor can support (you'll need to look in the monitor manual).  [Here is a how-to]("http://www.ubuntuforums.org/showthread.php?t=83973") concerning that.

---

