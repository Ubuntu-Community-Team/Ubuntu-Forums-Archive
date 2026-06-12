---
title: "Touchpad input pressure problem"
date: 2010-12-25
forum: Hardware
---

### Post by martank on 2010-12-25
Hey, I just installed ubuntu 10.10 on my macbook (4,1) and this is my first~ish time with linux. I'm mostly good for learning this stuff on my own, but I can't navigate very well because the touchpad seems to either require a lot more pressure than I'm used to, or it's detecting a lot of my touches as "accidental" input. 

Any help? 

Thanks!

---

### Post by martank on 2010-12-26
The solution for the jittery mouse is the same as the 10.04 solution mentioned here:

[https://help.ubuntu.com/community/MacBook4-1/Lucid](https://help.ubuntu.com/community/MacBook4-1/Lucid)

except the .conf file is now 

/usr/share/X11/xorg.conf.d/50-synaptics.conf

---

