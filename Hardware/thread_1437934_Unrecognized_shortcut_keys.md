---
title: "Unrecognized shortcut keys"
date: 2010-03-24
forum: Hardware
---

### Post by Hawk__0 on 2010-03-24
Kubuntu 10.04 doesn't recognize some of my shrotcut keys.  Is there any way I can force it to?  For example, it doesn't recognize my Fn + wireless key combination to turn the wireless on and off.  It doesn't recognize my brightness shortcut keys either. (fn + f6/7 or something)

---

### Post by Hawk__0 on 2010-03-25
bump

---

### Post by luisfpg on 2010-03-25
That depends a lot on which hardware and which kubuntu version you are using.
Try running the following commands and attaching the resulting files:
```

sudo lshw > lshw.txt
sudo lspci -vv > lspci-vv.txt

```
I've got a very similar issue ([http://ubuntuforums.org/showthread.php?p=9025417](http://ubuntuforums.org/showthread.php?p=9025417))

---

