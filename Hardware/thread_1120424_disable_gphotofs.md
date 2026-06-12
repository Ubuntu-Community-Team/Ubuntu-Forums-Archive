---
title: "disable gphotofs"
date: 2009-04-09
forum: Hardware
---

### Post by subajawa on 2009-04-09
I have an application to control cameras in ptp mode using libgphoto2. 

As soon as I connect the cameras, they get auto mounted because of fuser/gvfs/gphotofs. To run my app I have to call gvfs-mount  -s gphoto; <my_appname>. No other way I could run my app 

I would like to disable auto mount of gphotofs media alone. Is there any fuse or gvfs configuration to do this?

Thanks in advance.
Jawahar

---

### Post by nexius on 2011-02-02
perhaps you have already solved your problem. anyway you can disable automount through gconf-edit => app => nautilus => preferences and keepaway the flag on media_automount

Bye

Stefano

---

