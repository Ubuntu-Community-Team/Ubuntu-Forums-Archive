---
title: "Two Questions for You Guys. :D"
date: 2008-02-21
forum: Hardware &amp; Laptops
---

### Post by DM was on fire! on 2008-02-21
Numero uno: My dad bought two video cards, both the same: GeForce 7200 GS. I am absolutely pleased to know that they run on nVidia, especially after experiencing the problems that I have with an ATI Radeon 7000 (NEVER GET ONE OF THESE, EVER!). I searched it just for the heck of it, and it seems to only have a problem with Gutsy.
Would I have a problem with it if I'm running Dapper, or then upgrade up to Feisty (don't wanna run it on Gutsy until I'm sure)?
Also, what else would I have to do to make it work? I'm sure I'd have to install the nVidia drivers...

Numero dos: I really don't want to reinstall Ubuntu on this thing, and Xserver reconfiguration drives me up the wall. If I was to paste my xorg.conf file on this thread, would someone be able to tell me where I could edit my new video card in, and if so, what would it be?

Thanks. :D I think once my dad installs this thing I will no longer experience the crashes and lockups that I had.
MAYBE I CAN FINALLY RUN COMPIZ LIKE A NORMAL UBUNTU USER. XD

EDIT - I forgot a couple of things.
Gigabyte makes the video card, and I saw that pop up in the hardware compatibility thread, but it was a GeForce 7600. 
Also, I found the area which I'm supposed to edit, but I still don't want to screw anything up. ^^;;

---

### Post by nick_h on 2008-02-22
You should be able to install the nvidia drivers from System->Administration->Restricted Drivers Manager.

The easiest way to configure a new video card would be to run:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Make a backup of your xorg.conf file first so that you can restore it if necessary.
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

---

### Post by DM was on fire! on 2008-02-23
OH YAY. THANK YOU.
I'll definitely have to write that down. 

I saw the first command somewhere, but I don't remember where (probably here), and I wasn't sure if it was the command I wanted. 
Now I don't have to back up stuff, and I can upgrade. 8D (To Feisty, atleast, which is newer than what I have now)

---

### Post by nick_h on 2008-02-23
The command can be found in the comments at the beginning of the xorg.conf file.

---

