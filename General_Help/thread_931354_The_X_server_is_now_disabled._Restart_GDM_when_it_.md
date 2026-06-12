---
title: "The X server is now disabled. Restart GDM when it is configured correctly."
date: 2008-09-27
forum: General Help
---

### Post by Idanwin on 2008-09-27
My (other) computer isn't able to start X anymore.
"The X server is now disabled. Restart GDM when it is configured correctly."
What should I do?

---

### Post by ashmew2 on 2008-09-27
Which Graphic Card ?

---

### Post by anystupidname on 2008-09-27
For starters, I would probably try:

> sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.broken

sudo dpkg-reconfigure -phigh xserver-xorg

sudo /etc/init.d/gdm restart

(or restart)

If that doesn't help, we'll probably need to see
xorg.conf
/var/log/Xorg.0.log
lspci -v
lshw -C video
???

---

### Post by Poyntz on 2009-10-24
> **anystupidname said:**
> For starters, I would probably try:



(or restart)

If that doesn't help, we'll probably need to see
xorg.conf
/var/log/Xorg.0.log
lspci -v
lshw -C video
???

Good solution! But this resets the default resolution. How do you go back to the old resolution?

---

### Post by falconindy on 2009-10-24
You might try running without an xorg.conf at all and setting your resolution manually under System -> Preferences -> Display.

---

### Post by Poyntz on 2009-10-26
I only accidently renamed gdm to gpm, (didn't infact delete it!), no idea why I did this...

I managed to get xserver to kick into gear again, but I've again busted it - only from trying to launch nvidia-config - or some nvidia program that is supposed to roll to the nvidia driver or something like that. 

As such, I now have two problems (1) xserver won't kick into gear. (2) I can't get my nvidia graphics card to perform. If someone could help me fix these issues that would be great! At a guess, the first problem has something to do with my xorg.conf file... not sure what's wrong with it tho. I haven't been fiddling around with it

---

### Post by Poyntz on 2009-10-26
Deleted

---

