---
title: "Sony VAIO VGN-FZ250E Audio/Headphone Fix"
date: 2008-01-24
forum: Hardware &amp; Laptops
---

### Post by HariVenkata Lakshmi Kumar on 2008-01-24
Guys I succeeded in fixing the headphone not detecting on my VAIO. Here is solution for this issue

reinstall ALSA driver
run:
             [B]sudo apt-get install module-assistant
             sudo m-a update
             sudo m-a prepare
             sudo m-a a-i alsa
[/B]in terminal

and 
             **sudo gedit /etc/modprobe.d/alsa-base**

add the following line in opened config file

**options snd-hda-intel model=vaio position_fix=0**


now reboot your VAIO.

---

### Post by Bungholio the Bunghole on 2008-02-24
This totally worked, thank you!

---

### Post by L815 on 2008-02-25
The headphones now work, but the speakers don't mute.

---

### Post by panosp on 2008-05-19
didn't work for my vaio. [here]("http://ubuntuforums.org/showthread.php?p=4994381") is what i did to solve the issue

---

