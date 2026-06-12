---
title: "Change window manager?"
date: 2005-07-06
forum: Hardware &amp; Laptops
---

### Post by oggah on 2005-07-06
Hi, right now im running Ubuntu Hoary (minimal install) and XFCE4 on my Toshiba laptop. 
**I want  to change my window manager** to PWM [http://modeemi.fi/~tuomov/pwm/](http://modeemi.fi/~tuomov/pwm/)

Anyone knows how to do? - Please help.

---

### Post by manicka on 2005-07-06
It's available through apt/synaptic. 

I'd imagine you'd just install it then choose it from the sessions menu in the GDM login screen

---

### Post by Sye d'Burns on 2005-07-06
sudo apt-get install pwm

---

### Post by oggah on 2005-07-06
Ill try it out. Thanx guys.


edit:
Does work great. Have tried Fluxbox also. More free ram than xfce4, but still not as snappy and responsive as win2k.

---

### Post by manicka on 2005-07-06
[QUOTE=oggah]
More free ram than xfce4, but still not as snappy and responsive as win2k.[/QUOTE]

Really? I find these lightwght WM's extremely fast and responsive.

---

### Post by frodon on 2005-07-08
[QUOTE=manicka]Really? I find these lightwght WM's extremely fast and responsive.[/QUOTE]
I'm using gnome and install fluxbox successfully but I haven't found a way to replace metacity with fluxbox on gnome startup. Do you know how to do that ?
thanks

---

### Post by ozamosi on 2005-07-19
[QUOTE=frodon]I'm using gnome and install fluxbox successfully but I haven't found a way to replace metacity with fluxbox on gnome startup. Do you know how to do that ?
thanks[/QUOTE]
Sorry if this is old news for you now.
Start the configuration editor, open desktop, gnome, applications, window manager.
I got rid of metacity by unset:ing "current", and instead setting "default" to my WM of choice :)

---

### Post by frodon on 2005-07-19
[QUOTE=ozamosi]Sorry if this is old news for you now.[/QUOTE]Not at all !  I really appreciate the help. :razz: 
After setting the wanted WM do I need to restart Xserver ?
Which file contain the Gconf configuration ? (I always do a backup before modifying such things)

thanks ozamosi

---

