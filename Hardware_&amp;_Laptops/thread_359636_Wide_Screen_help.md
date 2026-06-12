---
title: "Wide Screen help"
date: 2007-02-12
forum: Hardware &amp; Laptops
---

### Post by marguz on 2007-02-12
Hello,
I've been trying to get my LG wide screen LCD display to work with Ubuntu Edgy (Feisty) for some time now. I can only get it to display 1024x768. This display can do 1440x900 @ 60Hz.

I'm using an IBM T60 with the Intel i810 (945GM) chipset.

I have followed guide after guide and I can never get this to work. Does anyone have this setup working and if so, can you please share it.

TIA.

---

### Post by Gummi on 2007-02-12
I almost exactly the same problem, the only difference is that I should be able to get my resolution up to 1280x800 60Hz. But instead it only goes to 1024x768 0Hz. :confused:

This problem is extremely annoying, and I would as well be very thankful if anyone knows what is wrong.

---

### Post by mitanc on 2007-02-12
I have some unknown LCD monitor from a Chinese factory that I purchased as a sample.  This thing is so ghetto that the remote doesn't work and if it turns off it takes an act of god to turn it back on.  Luckily I use it as a computer monitor and in order to get it to work 1280x768  kept playing with the hsync and vsync values in my xorg.conf file.  

Good luck.

---

### Post by Gummi on 2007-02-12
Is it possible that you can be more specific? Like to tell us it is possible to mess with those sync files int the xorg.conf files

---

### Post by -Phi- on 2007-02-12
I believe that most Intel chipset resolution issues can be solved by installing the package **915resolution** with your favourite package manager. More info: [http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/) (and I'm sure Google has more)

Hope it helps!

- Phi

---

### Post by Gummi on 2007-02-12
But the thing i that I don't want to change into 915 or anything like that, I actually want to get 800! :cry:

---

### Post by DrNick on 2007-02-12
I believe the '915' in the name refers to the Intel chipset, not the actual resolution you want to achieve.  Installing that package should allow you to change to that res :)

---

