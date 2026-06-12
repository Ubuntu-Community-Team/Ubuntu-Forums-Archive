---
title: "Problem with keyboard languages"
date: 2008-09-17
forum: General Help
---

### Post by igor55 on 2008-09-17
Well I was installing Ubuntu and I guess for some reason it recognized my keyboard as Czechia. Now when I've had problem with root password and everything since I use a MS natural USA keyboard. I finally was able to reset my password and fix everything but everytime I restart or shut down and turn it back on at later point, it goes back to inputting Czechia language. I already went to System->Preferences->Keyboard and changed it to USA there. It shows as USA but still types as if it were Czechia. Weird thing is if I add another USA Layout and delete previous USA layout it goes back to USA....it's weird but this is getting really annoying. Any way to permanently fix this. Thanks!

---

### Post by mb_webguy on 2008-09-17
Try typing "sudo dpkg-reconfigure xserver-xorg" in the terminal to reconfigure X.

---

### Post by zvacet on 2008-09-17
**system<admin>language support**>check language you want to get support to and below that you will see box in which you can select default language.

---

### Post by igor55 on 2008-09-17
> **zvacet said:**
> **system<admin>language support**>check language you want to get support to and below that you will see box in which you can select default language.
 Done this like 3 times now, it goes back to Czechia for some odd reason, even thought its telling me its using USA.

---

### Post by igor55 on 2008-09-17
> **mb_webguy said:**
> Try typing "sudo dpkg-reconfigure xserver-xorg" in the terminal to reconfigure X.

Thanks for this, I'll check if it did the trick after rebooting.

---

