---
title: "Graphics card problem?"
date: 2005-05-18
forum: Hardware &amp; Laptops
---

### Post by Leav on 2005-05-18
```
leav@leavsbox:~$ 3ddesk
Attempting to start 3ddesktop server.
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x30
Daemon started.  Run 3ddesk to activate.
Server not found after waiting 5 seconds.
Could not find server.
Try starting manually (3ddeskd)

leav@leavsbox:~$ 3ddeskd
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x30
Daemon started.  Run 3ddesk to activate.
leav@leavsbox:~$

```

this happens with scorched 3d too, and I havn't seen a 3d program work on my machine yet, so i'm guessing my graphics card isn't installed properly, right?

I have an "ATI Rage 128" card... anyway I can run a test program or something to see if opengl works or if the card isn't installed properly?

I don't fully understand the graphics architecture of an operating system, so execuse me if anything I said was really dumb... :)

-Leav

---

### Post by Leav on 2005-05-28
no answer yet.....

doesn't anyone have ANY suggestions?

---

### Post by PryGuy on 2005-05-28
[QUOTE=Leav]no answer yet.....
doesn't anyone have ANY suggestions?[/QUOTE]
I have nothing to add but want to ask Ubuntu gurus: Does 5.04 support ATI out of the box?

I use nVidia, and 5.04 supports it just fine, though you have to do something to activate the hardware 3D support:> sudo apt-get install nvidia-glx
sudo /etc/init.d/gdm stop
sudo nvidia-glx-config enable
sudo gdm startnVidia Rulez! :)

---

### Post by Leav on 2005-06-06
anyone know of a similar pacakge for the "ati rage 128 pro"?

---

