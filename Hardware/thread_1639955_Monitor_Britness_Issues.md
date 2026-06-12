---
title: "Monitor Britness Issues"
date: 2010-12-07
forum: Hardware
---

### Post by dansimon on 2010-12-07
I'm running xubuntu 10.10 on my hp g61. A few minutes after installation the monitor 
dimed, and the brightness never reappeard. I have fiddled around in the power managment settings and screensaver setting to try and remedy this problem, but to
no avail. 
Any help here would be greatly appreciated. PS! is there any way of manualy setting
monitor brightness with a terminal command??

---

### Post by dargaud on 2010-12-07
Check your bios, as there are sometimes options for brightness settings right in there (Auto, eco, max, etc). There used to be some brightness setting tools in the repositories but i don't see them anymore.

---

### Post by dansimon on 2010-12-07
Could you perhaps be a little bit more spesific? do you mean i should edit the grub.cfg file in /boot/grub? I tried having a look there, but i didn't find anything usefull.

---

### Post by dargaud on 2010-12-07
Not grub, I mean the BIOS which shows very quickly right after boot. keep pressing Del / F1 / F2 / F10 / F11 or F12 when the PC boots if you don't see any message telling you what to press to enter the BIOS setup menu. Every brand has a different key !

---

### Post by dansimon on 2010-12-14
OK, i tried monkeying around in the bios settings, but i didn't have any luck. Heres a weird thing though; a few days ago the monitor suddenly whent bright and sparkly all by itself. Then just risently it dimed down agein.
There seems to be a kind of pattern here, every time the coputer hibernates or suspends, the monitor auto-dims and does not brighten afterwards (with exeptions...).
 
Isnt there some terminal command or something to adjust monitor brigtness manualy?
I mean this is Linux right? The OS where you can tweek everything amaginable, and then some! - Is there really no way to adjust monitor brightness ???

---

### Post by brokenromeo on 2010-12-14
You could add the brightness applet to the panel...right click, add to panel, find the brightness applet...you could be having a hardware issue though with the screen or connector.

---

### Post by dansimon on 2010-12-14
Is this a part of the gnome-applet package? How do you use gnome applets in Xfce
(im using Xubuntu).

---

### Post by dansimon on 2010-12-14
Ok, i figured it out (you have to use xfapplet). It works, thanx a bundle :D:popcorn:

---

