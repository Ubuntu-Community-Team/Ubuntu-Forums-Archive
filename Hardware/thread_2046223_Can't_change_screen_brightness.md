---
title: "Can't change screen brightness"
date: 2012-08-22
forum: Hardware
---

### Post by therog726 on 2012-08-22
Hi guys,

I would like to change my screen brightness level but the slider under "Brightness and Lock" settings doesn't work.

I suspect its a (hybrid) graphics issue since I've had quite a bit of trouble getting them to work. I have a hp dv6 with sandy bridge i5-2340M and hybrid Intel 3000/AMD 6700M.

I have followed various posts and wikis (like [this one]("http://ubuntuforums.org/showthread.php?t=1930450&highlight=AMD%2FIntel+Hybrid+Graphics") and [this one]("http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29")) trying to get these cards playing together nicely. I can install catalyst etc and get it going but as soon as I change to integrated graphics
```
sudo aticonfig --px-igpu
```
xserver craps out and I can't get into any desktop shell.

I'm running precise and currently have catalyst 12.6 installed.

Can anyone help me? I can post more info if you need it, just let me know.

Cheers

---

