---
title: "Old monitor"
date: 2005-08-15
forum: Hardware &amp; Laptops
---

### Post by hiperbou on 2005-08-15
I have an old monitor wich can't support any higher resolution from 1024x768 with 16 COLOURS (not 16 bits).
I can choose the Ubuntu's resolution at the instalation? or change it before starting the system?

---

### Post by PeP on 2005-08-15
it should be detected automatically. Did you try the live CD?

---

### Post by hiperbou on 2005-08-15
I haven't download it yet. But I've tried on a knoppix live-cd wich set the display resolution to 1024++ and the monitor was unable to show anything coherent..
In this case knoppix can be started selecting the resolution by entering some params turning it at 800x600 works well..

---

### Post by PeP on 2005-08-15
If the installation disk shows up with a readable interface, you will at worst have problems in gnome/kde, and those problem can be solved in console mode (switch with ctrl+alt+F1)

then a 
```
sudo dpkg-reconfigure xserver-xorg
```
will ask you a lot of questions about your screen, graphic card, mouse ...
select defaults if you don't know, and set your screen resolutiona and color-depth according to your screen.

I cannot remember if those question are asked during tje instalation or not :-?

---

