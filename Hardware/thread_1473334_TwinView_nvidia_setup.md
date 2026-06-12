---
title: "TwinView nvidia setup"
date: 2010-05-05
forum: Hardware
---

### Post by thorob on 2010-05-05
Hi
I'm trying to set up twin view with an nvidia driver.
It works fine but when I click on "Save" I get the message 

"Failed to parse existing X config file '/etc/X11/xorg.conf'"

I then deleted xorg.conf, and created new file with touch.
But get the same message. I even did a chmod 777 on /etc/X11/xorg.conf
but that didn't help either.

Any advice?

---

### Post by dino99 on 2010-05-05
work on my end with nvidia-settings

---

### Post by Grenage on 2010-05-05
You're running nvidia-settings with sudo/gksudo, I presume?  If you preview the code, then manually copy it into xorg.conf, does it work then?

---

### Post by realzippy on 2010-05-05
...the old bug.

[http://ubuntuforums.org/showthread.php?t=1312435](http://ubuntuforums.org/showthread.php?t=1312435)

Delete existing xorg.conf:

```
sudo rm /etc/X11/xorg.conf
```

then make a new one (not with touch):

```
sudo nvidia-xconfig
```

Thats it.

---

### Post by thorob on 2010-05-05
Combining Grenage's (gksudo) and realzippy's solutions worked, thanks a lot!

---

