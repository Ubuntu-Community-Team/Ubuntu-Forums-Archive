---
title: "need to mount USB devices"
date: 2008-10-01
forum: General Help
---

### Post by benner on 2008-10-01
i did a barebones install from a minimal cd then added lxde on top of it. all is well except that i don't have any plug and play with usb devices. when i open gparted, i can see and edit partitions etc... from a flash drive that i plug in but i can't access the files from the file manager (PCMan).
i see a number of options listed in the repos, tried a couple and nothing happened. can anyone recommend a simple one that won't take up too much space?

---

### Post by olejorgen on 2008-10-02
The only automounter I've used is gnome-volume-manager. That might drag in a lot of gnome deps.

Do you know how to mount manually?

---

### Post by kpkeerthi on 2008-10-02
Looking at [dependencies]("http://packages.ubuntu.com/hardy/gnome-volume-manager") of gnome-volume-manager, it appears that it pulls quite a 'lot' of GNOME packages.

I suggest you use [ivman]("http://packages.ubuntu.com/hardy/ivman"). Much lighter.

---

