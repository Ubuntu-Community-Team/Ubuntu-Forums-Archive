---
title: "Mercury TV Card not detected"
date: 2005-07-05
forum: Hardware &amp; Laptops
---

### Post by gforces on 2005-07-05
I have a mercury TV card which ubuntu failed to pick up on installation. I've only been using linux for a couple of weeks and would appreciate some guidelines for getting it to work. I believe the tuner is Phillips but the model # is not obvious from the Kobian/Mercury website.
Thanks in advance.

---

### Post by liarsenic on 2007-04-30
Easy fix, to make it work run (in root):
rmmod saa7134
modprobe saa7134 card=3 tuner=39

It will most likely work. If it does, read the rest to put these commands at startup so you wont need to execute them everytime you want to watch tv.

First, undo any changes to any config files you may have modified to try to make it work. Log in as root. In your startup script (in my case its boot.local) in /etc/init.d i put these lines and it works perfect.

rmmod saa7134
modprobe saa7134 card=3 tuner=39

What happens is that the driver settings the kernel assigns are not properly configured and if you just modprobe without rmmodding, it'll add to the mess (if it even works).

NOTE FOR XGL/COMPIZ USERS: If you're using compiz/xgl you will notice that the image is gargled (in kdetv anyway) but not when Desktop Effects are disabled. In kdetv, go in Settings>Configure kdetv. Now go in the Image Filters tab, uncheck Overscan.

---

