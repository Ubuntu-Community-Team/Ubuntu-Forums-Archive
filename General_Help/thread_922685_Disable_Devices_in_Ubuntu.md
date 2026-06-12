---
title: "Disable Devices in Ubuntu"
date: 2008-09-17
forum: General Help
---

### Post by SSVegito888 on 2008-09-17
I am new to Linux and am using Ubuntu 8.04 Hardy.

I am wanting to disable my webcam and microphone.  I would also like to be able to re-enable them when I need them.


How do I do this?

I would like to use a GUI if possible.

I am not against downloading a frontend or an application to be able to use a GUI.


If Ubuntu does not come preinstalled with a GUI for this, if you can, please let me know where to find one.


Thanks,

SSVegito888

---

### Post by karlr42 on 2008-09-17
well, type ```
lsmod
``` in a terminal. That shows you the modules you're using. Try to find the one for the webcam(you can say```
modinfo <name>
``` to get more info).
Once you have it, ```
sudo gedit /etc/modprobe.d/blacklist
```
and add blacklist <name> at the end. Then reboot, and the webcam should be deactivated. Not very elegant, I know :(  I'm not sure if there's a GUI to do it. I might write a script to do it if you find the name

---

### Post by SSVegito888 on 2008-09-18
Thanks

---

