---
title: "Problems mounting USB hard drive"
date: 2005-01-30
forum: Hardware &amp; Laptops
---

### Post by Viro on 2005-01-30
OK, I know this has been asked a lot, but this has got nothing to do with NTFS support :).

I've got a laptop hard drive that is housed in a casing that I access using USB 2.0. When I plug it into my laptop, it mounts the drive and the icon appears on the desktop. After about 5 seconds, it unmounts automatically. A while later, it mounts again. And unmounts. And mounts.... ad infinitum.

It works fine in Debian so i know it isn't the fault of the hard drive. The thing is, when it's unmounted, even fdisk says there is nothing on /dev/sda, where the drive should be. 

Anyone able to shed some light on this?

---

### Post by poofyhairguy on 2005-01-31
[QUOTE=Viro]OK, I know this has been asked a lot, but this has got nothing to do with NTFS support :).

I've got a laptop hard drive that is housed in a casing that I access using USB 2.0. When I plug it into my laptop, it mounts the drive and the icon appears on the desktop. After about 5 seconds, it unmounts automatically. A while later, it mounts again. And unmounts. And mounts.... ad infinitum.

It works fine in Debian so i know it isn't the fault of the hard drive. The thing is, when it's unmounted, even fdisk says there is nothing on /dev/sda, where the drive should be. 

Anyone able to shed some light on this?[/QUOTE]


I can take a swing at it. Ubuntu uses Project Utopia for its automounting. The project is fairly new, and you hit a bug in it.

[http://lug.mtu.edu/slides/project_utopia.html](http://lug.mtu.edu/slides/project_utopia.html)

File a bug report to the big Ubuntu devs...see if it can get fixed. Also try disabling the gnome-volume-manager, and manually mounting drives yourself.

---

