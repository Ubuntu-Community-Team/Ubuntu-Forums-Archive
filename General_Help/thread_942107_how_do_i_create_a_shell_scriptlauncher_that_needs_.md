---
title: "how do i create a shell script/launcher that needs sudo without having to type passwd"
date: 2008-10-08
forum: General Help
---

### Post by bigdee973 on 2008-10-08
how do i create a shell script/launcher that needs sudo without having to type passwd for it? im trying to create a shell script to launch sudo nautilus...

#!/bin/bash
sudo nautilus

i give it chmod +x but the thing is when i double click it and choose "RUN" it doesnt run because it needs a password.how can i write a script to automatically give it the password so that it could run at once? is it posible or is there another successful way to create a launcher for sudo nautilus???

---

### Post by bodhi.zazen on 2008-10-08
First you should use gksu for graphical applications.

Second, you need to use "visudo"

[http://www.sudo.ws/sudo/man/sudoers.html](http://www.sudo.ws/sudo/man/sudoers.html)

---

