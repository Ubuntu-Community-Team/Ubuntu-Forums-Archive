---
title: "enable/disable touchpad hotkey brokes, maybe a recent updates"
date: 2011-10-24
forum: Hardware
---

### Post by FelipeAF on 2011-10-24
Hi, i use ubuntu 11.10. the touchpad enable/disable shortcut was working until some days ago. Today, not working more, maybe a recent update broken.
I have a Lenovo G470 notebook and a 64 bits system The hotkey here is FN+F6. In xev, no event send when i press Fn+F6, others hotkeys works.
In windows, this hotkeys works

---

### Post by www.rzr.online.fr on 2011-11-01
I confirm this is also happening in debian using custom kernel :


 cat /proc/version
Linux version 3.1.0+ (root@lap) (gcc version 4.6.2 (Debian 4.6.2-3) ) #5 SMP Tue Nov 1 02:15:33 CET 2011


Have you tuned your touchpad to support multitouch etc ?


It used to work before , note that Fn up/dn works too


BTW, I have a g470 too , are your fans stopping ?

-- 
[http://rzr.online.fr/q/lenovo](http://rzr.online.fr/q/lenovo)

---

### Post by kholis on 2011-12-13
I have the same problem on Lenovo G460. Fn+F6 key (enable/disable touchpad) doesn't work on ubuntu 11.10.

I think it's a kernel problem.

thanks

---

### Post by lenovopro on 2012-05-19
in my case this works but the multitouch no, any sugestion?

---

### Post by www.rzr.online.fr on 2012-07-06
multitouch is working on my debian system ...

---

