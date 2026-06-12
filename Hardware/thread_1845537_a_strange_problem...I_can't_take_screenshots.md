---
title: "a strange problem...I can't take screenshots"
date: 2011-09-17
forum: Hardware
---

### Post by Shadowmourne on 2011-09-17
I can't take screenshots on my laptop with 2720QM & HD graphics 3000
When ever I press PRINT SCREEN,I can only get my wallpaper.
if I press alt+PRINT SCREEN, I can only get a part of my wallpaper......
I‘ve tried ubuntu 11.04 11.10 and fedora 15, all of those OS have this problem.

[ATTACH]202336[/ATTACH]

[ATTACH]202337[/ATTACH]

[ATTACH]202338[/ATTACH]

---

### Post by Shadowmourne on 2011-09-17
Could someone help me?

---

### Post by bapoumba on 2011-09-17
Just to make sure, can you take ascreenshot with gnome-screenshot from the command line or from the menu?
options are listed in the manual:
```
man gnome-screenshot
```

---

### Post by Shadowmourne on 2011-09-17
> **bapoumba said:**
> Just to make sure, can you take ascreenshot with gnome-screenshot from the command line or from the menu?
options are listed in the manual:
```
man gnome-screenshot
```

at first I got this message
DEBUG: The GetProfileForWindow request failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.ColorManager was not provided by any .service files 
 then I install the gnome-color-manager
 now when I running gnome-screenshot from a terminal
 I got nothing...

---

### Post by bapoumba on 2011-09-17
Googling for your error, I found your thread at the fedora forums, looks they asked the same question ;)

Are you using several monitors ?
[https://bbs.archlinux.org/viewtopic.php?pid=970756](https://bbs.archlinux.org/viewtopic.php?pid=970756)

---

### Post by Shadowmourne on 2011-09-18
I've read this thread in archlinux forums before
but all of the way in this thread didn't work
and I'm using only one monitor...

---

### Post by bapoumba on 2011-09-18
What video hardware and drivers are you using ?

In the mean time, most common bugs (although probably not related):
[https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/642792](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/642792)
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/771875](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/771875)
[https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/29894](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/29894)
[https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/743176](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/743176)
[https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/510073](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/510073)

---

### Post by Shadowmourne on 2011-09-18
> **bapoumba said:**
> What video hardware and drivers are you using ?

In the mean time, most common bugs (although probably not related):
[https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/642792](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/642792)
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/771875](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/771875)
[https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/29894](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/29894)
[https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/743176](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/743176)
[https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/510073](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/510073)

Intel HD Graphics 3000 in i7 2720QM ES2(Q154)
I think the driver is already integrated in kernel
I also installed Mesa 7.11 and xf86-video-intel-2.16.0

---

