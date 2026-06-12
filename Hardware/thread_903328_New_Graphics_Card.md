---
title: "New Graphics Card"
date: 2008-08-28
forum: Hardware
---

### Post by bipolaric on 2008-08-28
My Current Graphics Card is an XFX GeForce 7300GT 128mb

Sometimes when I boot-up the login screen is all messed up, can anyone tell me why this is, ALSO, I was thinking of upgrading my Graphics Card to a....
XFX 512MB 9800GT

Would the 9800GT be Ubuntu compatible ?

Thanks - MArk :)

---

### Post by nicedude on 2008-08-29
You should try using envyng to download and install a newer driver for you as a Ubuntu's one it uses by default is rarely the one that is best.

Here is the command to install envyng

sudo apt-get install envyng-gtk

And here is a command to launch it

sudo envyng-gtk

Once you get it open just select Nvidia and install driver and let it choose everything for you, also when it asks if it should configure your xorg.conf file for you say yes. Then just press Ctrl+Alt+Backspace and that will relaunch the xserver and you should be good to go.

Hope that helps

---

### Post by Crafty Kisses on 2008-08-30
Post the results > glxinfo

---

