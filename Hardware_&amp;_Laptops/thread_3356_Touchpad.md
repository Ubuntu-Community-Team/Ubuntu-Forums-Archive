---
title: "Touchpad"
date: 2004-11-05
forum: Hardware &amp; Laptops
---

### Post by Zariski on 2004-11-05
Hello.

After installing Ubuntu, my touchpad works as it should; unfortunately! Isn't it possible to disable the option that touching the pad works as a mouse click?

-- 
Zariski

---

### Post by DoubleDangerClub on 2004-11-05
I had the same problem and will be posting a how-to dealing with synaptics touchpads tomorrow! :)

---

### Post by daniels on 2004-11-06
In the meantime, run synclient -l; you should get a whole bunch of output like:
```
Button1Click = 1
```
or something.

Run synclient Button1Click = 0, to disable it.  I can't remember what the option's actually called, because I don't have a touchpad.

---

### Post by DoubleDangerClub on 2004-11-10
My how-to is located here:

[http://www.ubuntuforums.org/showthread.php?p=14604#post14604](http://www.ubuntuforums.org/showthread.php?p=14604#post14604)

---

