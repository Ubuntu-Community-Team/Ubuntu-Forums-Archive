---
title: "via openchrome 3d problems"
date: 2007-10-09
forum: Hardware &amp; Laptops
---

### Post by chaosmachine06 on 2007-10-09
So, this is the second time I've tried to compile the openchrome driver onto my computer, and this is the second time 3d rendering has failed. I get through the instilation procedures followed from this guide [https://help.ubuntu.com/community/OpenChrome?highlight=%28openchrome%29](https://help.ubuntu.com/community/OpenChrome?highlight=%28openchrome%29) Just fine until I do glxinfo | grep rendering wich is when I get this:

X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  16
  Current serial number in output stream:  17

any thoughts?

---

### Post by chaosmachine06 on 2007-10-09
bump for unsolved

---

### Post by Syke on 2007-10-10
Why not use the pre-compiled package? Enable Feisty Backports, then "sudo aptitude install xserver-xorg-video-openchrome" and make sure Driver is set to "via" in xorg.conf.

---

