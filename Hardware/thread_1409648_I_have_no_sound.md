---
title: "I have no sound"
date: 2010-02-17
forum: Hardware
---

### Post by nmegabyte on 2010-02-17
Hi guys i am kinda noob i just installed a new ubuntu 9.1 on my Asus G1s laptop and i have no sound when i play the music i installed all the proper drivers and plugins for mp3 and video but still no sound any help and if there is a way to fix it, explain me how to fix it, i am noob. First time using ubuntu. Ok a little change in my problem there is no sound in laptop speakers but when i plug in headphones i have sound when i unplugged them there is no sound from laptop speakers.

---

### Post by pi/roman on 2010-02-17
Open a terminal and type "alsamixer". You can fiddle with the settings there and maybe you'll be able to fix your problem.

---

### Post by jackportd on 2010-02-18
Hi,
Try another account or root access with something like an su login. It sounds like the package changed account settings erroneously. You may need to reset the machine password by booting from another device.

---

### Post by nmegabyte on 2010-02-19
well it still does not work i tried to fix it like u told me still doesnt work.. And also i  cant play GIF files they are not animating.

---

### Post by pi/roman on 2010-02-19
Try installing linux backport modules if you have not already then look at this search and see if you find anything useful, or vice-versa maybe:
[http://www.google.com/#hl=en&source=hp&q=%22options+snd-hda-intel+model+%3D+m51va+position_fix+%3D+0%22&aq=f&aqi=&oq=&fp=79a46ede2c2a175d](http://www.google.com/#hl=en&source=hp&q=%22options+snd-hda-intel+model+%3D+m51va+position_fix+%3D+0%22&aq=f&aqi=&oq=&fp=79a46ede2c2a175d)

---

