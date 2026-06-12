---
title: "Just got an lcd tft monitor. Ubuntu does not identify properly"
date: 2008-01-10
forum: Hardware &amp; Laptops
---

### Post by smacfarl on 2008-01-10
So the monitor is an SVA VR-17B.

Forgive me for asking such a noob question. But how do I get Ubuntu to display properly?

I looked for the model in the system/administration/dcreen and graphics admistration widget. But its not there. 

Ubuntu has decided I have a plug and play monitor. So while the screen is visible. It looks terrible. 

Maybe i should change xorg? all advice welcome.

---

### Post by taurus on 2008-01-10
You probably just need to reconfigure your X server for the new monitor.  Open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then, restart X again with <Ctrl><Alt>Backspace.

---

### Post by dark_phantom on 2008-01-10
> **taurus said:**
> You probably just need to reconfigure your X server for the new monitor.  Open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Then, restart X again with <Ctrl><Alt>Backspace.

Dude, thanks so much.  I've been trying to get my Samsung 245T monitor to work and this did it.

---

