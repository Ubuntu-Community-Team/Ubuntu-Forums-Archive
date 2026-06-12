---
title: "Wine + wine-doors. Wine-doors doesn't want to start..."
date: 2009-05-23
forum: Installation &amp; Upgrades
---

### Post by semyazz on 2009-05-23
I've tried to install wine + wine-doors, and everything was good untill i tried to lunch wine-doors... It is lunching and after a moment it just shutdowns. 
When i tried to lunch it via console... i saw this error:
```

/usr/share/wine-doors/src/utils.py:7: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import md5
Traceback (most recent call last):
  File "/usr/bin/wine-doors", line 21, in <module>
    from wine import wine
  File "/usr/share/wine-doors/src/wine.py", line 14, in <module>
    from utils import GetCDMountPoint, getwinecoloursfromgtk, GetXkbmap
  File "/usr/share/wine-doors/src/utils.py", line 11, in <module>
    import gconf
ImportError: No module named gconf

```
I've installed gconf2 packages...
Any ideas how to solve it?

---

### Post by semyazz on 2009-05-23
It seems i've solved this problem...

So for everyone who will face this same error...

Solution:
install python-gconf
apt-get install python-gconf

---

### Post by sysst on 2009-10-25
> **semyazz said:**
> It seems i've solved this problem...

So for everyone who will face this same error...

Solution:
install python-gconf
apt-get install python-gconf
Thanks, I had the same error this python-gconf solved it.
Strange, I had wine-doors working earlier, but this happened after I updated to a newer version of WINE.

---

### Post by amr2205 on 2010-03-06
> **semyazz said:**
> It seems i've solved this problem...

So for everyone who will face this same error...

Solution:
install python-gconf
apt-get install python-gconf

Thanks! It solve my problem! ;)

---

