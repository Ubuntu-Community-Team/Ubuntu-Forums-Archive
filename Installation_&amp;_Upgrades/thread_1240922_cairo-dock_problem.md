---
title: "cairo-dock problem"
date: 2009-08-15
forum: Installation &amp; Upgrades
---

### Post by sonusikka on 2009-08-15
hi...
how to install motion blur plugins, when i go configure i see only 2plugins namely dbus and gnome integration  and also i want to remove that ugly black background when i point to dock, how is it possible.
the theme I'm using for cairo is tux n tosh!!

---

### Post by sonusikka on 2009-08-15
hey....ny1 in this community has ny idea ....how to fix this problem especially that black ugly background

---

### Post by sonusikka on 2009-08-16
here is detailed config... ##post 673
[http://ubuntuforums.org/showthread.p...61#post7793761](http://ubuntuforums.org/showthread.p...61#post7793761) 
 compiz was running smoothly in hardy heron version, but is having hard time in jaunty!!

---

### Post by toiletpaper14 on 2009-08-16
To remove the Background, you have to enable desktop (visual) effects, and you have to be using "Cairo-Dock (no openGL)". It has only 4 or 5 plugins less but it's a 100 times more stable AND there's no black background.

---

### Post by sonusikka on 2009-08-16
I,m not able to enable that normal or extra desktop effects!!

---

### Post by toiletpaper14 on 2009-08-16
Have you installed the 3D acceleration driver? 
You can probably find it in System-Administration-Hardware Drivers.

---

### Post by AlanR8 on 2009-08-16
You don't have to run Compiz to use Cairo Dock but in my experience you get the ugly black box/border around the dock. I'm running Karmic A4 and all is well but I found on this Sony laptop that when I enabled effects the cpu load increased. Also, glxgears shows a CONSIDERABLE reduction in performance.

The answer for me was to run metacity instead:

[http://xwinman.org/metacity.php]("http://xwinman.org/metacity.php")

Metacity is a light weight compositor and once running the black border goes. To enable metacity, from a terminal:

> sudo metacity -c

and off you go!

---

