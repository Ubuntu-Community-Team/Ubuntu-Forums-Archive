---
title: "Missing Background and icons on boot"
date: 2008-07-25
forum: General Help
---

### Post by MissMachine on 2008-07-25
I searched the threats and there was one similar but the question was really never answered. Every once in a while when I boot up the desktop background and the desktop icons never load. It happens on probably 15% of my boots. I've read that it might have something to do with gnome-panel, but I'm not entirely sure. Anyone out there know what's causing this? I'm running hardy, gnome 2.22.3.

---

### Post by geirha on 2008-07-25
It's a bug in nautilus, the file manager. 
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/218070](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/218070)

It used to happen occasionally to me as well in gutsy, but I haven't noticed it since I upgraded to hardy. An inconvenient workaround is to open a terminal when it happens, and run ```
killall nautilus
``` which will kill the currently running, but failed, nautilus. A new one will be spawned automagically, which should draw the desktop and icons again.

---

### Post by MissMachine on 2008-07-25
Wow awesome that took care of it. Is there any way to fix this problem longterm, like a update to nautilus? I have installed 1:2.22.3-0ubuntu2 according to SPM. If not thanks for the help either way!

---

