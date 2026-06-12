---
title: "how to setup my external monitor as the primary display?"
date: 2010-07-06
forum: Hardware
---

### Post by bhuvi on 2010-07-06
i want to setup my external monitor as the primary display and i want my notification bubbles to pop up in the external display?
how can i do it in my ubuntu 10.04?

---

### Post by djinnkeeper on 2010-07-06
Hm.  I assumed someone would have jumped on this one.  I don't know but I'll take a stab or two at it..

If you're using nvidia or ati, try to use their respective tools to set up a multi-monitor desktop.  If you're not using a proprietary driver, there is System > Preferences > Monitors .. sorry I don't know the answer, but I'd like to see you get it solved.. so I'll help you bump it around. ;)

---

### Post by bhuvi on 2010-07-06
I have integrated intel graphics controller and there is only option to change the location of external display and there is no option to set the primary display

---

### Post by bhuvi on 2010-07-06
I have integrated intel graphics controller and there is only option to change the location of external display and there is no option to set the primary display in the monitor preferences

---

### Post by djinnkeeper on 2010-07-06
[/showthread.php?t=268712]("http://ubuntuforums.org/showthread.php?t=268712")
[/showthread.php?p=9043474]("http://ubuntuforums.org/showthread.php?p=9043474")
and this.. [http://ozlabs.org/~jk/docs/mergefb/]("http://ozlabs.org/%7Ejk/docs/mergefb/")

..appear to at least touch upon this subject.. you might end up having to mess with xorg.conf, but maybe not.

---

### Post by bhuvi on 2010-07-06
> **djinnkeeper said:**
> 
[/showthread.php?p=9043474]("http://ubuntuforums.org/showthread.php?p=9043474")


..appear to at least touch upon this subject.. you might end up having to mess with xorg.conf, but maybe not.

Thanks that worked

---

