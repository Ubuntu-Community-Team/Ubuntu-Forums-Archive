---
title: "Disable laptops mouse"
date: 2006-10-06
forum: Hardware &amp; Laptops
---

### Post by Tachyon_ on 2006-10-06
So my problem is the drifting and randomly moving laptop mouse with my old and cheap Compag Armada laptop. I thought it was a software problem, but I discovered it to be a hardware one yesterday. I'd like to disable the stick style mouse and use only external mouse as the inbuilt makes system usable for every second 10 minute perioid.
I searched forum, after that I commented the synaptics touchpad sections out int the /etc/X11/xorg.conf and rebooted. How ever, nothing happened (EDIT: Everything was back to normal). This is the issue where I didn't find answer that many others were experiencing too.

Please, everything else is perfect, and Im hoping for a software solution for this hardware problem as Im not sure what kind of damage I can do with hardware solution (pulling the thing out). :-k

---

### Post by jpatt on 2006-10-13
I still have that problem as well. 6.0.6 plus Dell Latitiude 650 Mhz. I have a PS/2 ext mouse connected with the same symptoms. I too would like to disable stick and touchpad. Nothing in Xorg.conf seems to do the trick. The mouse still my only problem.

---

### Post by Raoul Duke on 2006-10-13
Try

sudo modprobe -r psmouse

---

