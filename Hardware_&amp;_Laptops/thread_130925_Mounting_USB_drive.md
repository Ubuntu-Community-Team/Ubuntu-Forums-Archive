---
title: "Mounting USB drive"
date: 2006-02-15
forum: Hardware &amp; Laptops
---

### Post by Elrohir on 2006-02-15
ehmm... not sure if this thread goes here but anyway, here's my question...

Gnome mounts automatically any drive (aka CDROMs, USB drives and so), but XFCE doesn't... what the the command for mounting it (the one that Gnome uses)?

dont try the ```
sudo mount -t usbfs /dev/*** /media/***
```one... already done it and it is not the one I'm looking for...

---

### Post by damo21 on 2006-02-16
gnome-volume-manager i think, its run as a service.  I also use xfce, i think if you enable the "gnome services" in the xfce settings it should work.

Im also having trouble with the automount feature but using gnome... it seems that there might be a bug where it tries to mount /dev/sda instead of /dev/sda1 where the actual partition starts.

---

### Post by Elrohir on 2006-02-17
but I have Gnome Services enabled and no go... do I have to enable the KDE services too?

---

### Post by Elrohir on 2006-02-22
thanx!

---

