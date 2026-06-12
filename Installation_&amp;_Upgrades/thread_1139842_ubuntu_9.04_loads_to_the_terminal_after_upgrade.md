---
title: "ubuntu 9.04 loads to the terminal after upgrade"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by martez81 on 2009-04-27
I have upgraded ubuntu 8.10 to 9.04 and now ubuntu loads in in the terminal mode. Has anybody discovered this issue?

---

### Post by mikewhatever on 2009-04-27
I don't think there is a singe possible issue. Can you login and try the following commands:
sudo startx
sudo /etc/init.d/gdm start
If errors appear, try to copy them and post here. You should also tell about your graphics hardware.

---

### Post by martez81 on 2009-04-27
Thanks for response. I tried to do what you wrote but with no success. Any good hint how to copy errors from terminal window?

---

### Post by martez81 on 2009-04-27
Solved. 
I thought it will turn out to be much more complicated than that. What I did is I run the recovery mode and chose "try to auto repair graphic problems". Now everything works fine again!

---

