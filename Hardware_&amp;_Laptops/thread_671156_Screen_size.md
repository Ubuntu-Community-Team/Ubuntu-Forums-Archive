---
title: "Screen size"
date: 2008-01-18
forum: Hardware &amp; Laptops
---

### Post by ogden-quin on 2008-01-18
Yes someone else whinning about the screen size on their laptop.

I have a lcd cappable of showing 1920x1200 but ubuntu only seems to want to display@ 1204x768 even with the ristricted drivers.

"I just want it to work!"

NVIDIA GeForce Go 7950 GTX
Inte Core2CPU T7600 @ 2.33GHz x2

I'am an artist not a computer type person so have no knowledge at all, Is there a way to get my lcd to perform properly?

Please help me I'm about to reinstall windows !

---

### Post by jerrykenny on 2008-01-18
Can you go to system-administaration-screens&graphics . . . . . before you do anything there first open a terminal and type the following command

sudo cp /etc/X11/xorg.conf  /etc/X11/xorg.conf.good


DONT reinstall windows !    gimp is excellent for photo manipulation, and there is so much graphic-art stuff in linux its worth persevering

---

### Post by ogden-quin on 2008-01-19
Many thanks I will try this!

---

### Post by ogden-quin on 2008-01-19
No this didn't work!

Any other suggestions?

---

### Post by c0met on 2008-01-19
What JerryKenny was getting you to do was to make a backup copy of the configuration of your screen so that in case anything happened, you could get it back. If you are playing around with the monitor, always use the "test" option rather than just clicking "ok". If "test" doesn't work, the monitor will restore to previous settings.

It might be that you have to use [COLOR="DarkRed"]**Restricted Drivers Manager**[/COLOR]. To do this, you first need to check that in [COLOR="Purple"]**System >> Administration >> Software Sources**[/COLOR] you have a check-mark against [COLOR="DarkRed"]**Propriety Drivers by Devices**[/COLOR] and **[COLOR="DarkRed"]Software restricted by copyright or legal issues[/COLOR]**. If you have to engage these, you will need to reload your repositories.

Once the above is done, go to [COLOR="Purple"]**System >> Adminstration >> Restricted Drivers Manger**[/COLOR] and see if there is anything there that needs to be enabled. If the **[COLOR="Purple"]Restricted Driver Manager[/COLOR] **does not open, it simply means that your system has decided that you have no need to use it.

---

