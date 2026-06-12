---
title: "WIFI card not working under ubuntu 13.04"
date: 2013-12-06
forum: Hardware
---

### Post by penuel1310 on 2013-12-06
Hi Guys, please help me fix my problem..

 My 'Linksys wireless-G "WPC54G V3" notebook adapter ' is not working. When i attach it to my laptop, my computer freezes and takes me to tty1, and i have to hard restart my computer.

---

### Post by mikewhatever on 2013-12-06
There is no fix for the first one. Geforce 7400 is too old for Unity. You should be using 12.04 with Unity-2d or something lighter like XFCE.

---

### Post by penuel1310 on 2013-12-06
i am not using unity anymore, i'm running gnome shell

---

### Post by mikewhatever on 2013-12-06
...but Gnome Shell also requires a decent graphics card. You may want to search for it, but I doubt the Geforce 7400 perfrms any better with Gnome Shell.

---

### Post by penuel1310 on 2013-12-15
I fixed my wifi... I had to downgrade my kernel from 3.8 to 3.4 and wifi worked.
For my graphics card.... I installed Nouveau drivers and gala windows manager. it is still a bit glitchy, but now i have animation...

---

