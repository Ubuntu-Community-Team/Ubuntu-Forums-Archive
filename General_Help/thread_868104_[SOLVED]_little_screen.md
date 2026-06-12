---
title: "[SOLVED] little screen"
date: 2008-07-23
forum: General Help
---

### Post by pikabuntu on 2008-07-23
I started ubuntu and the screen was small.
It said its running in limited graphics mode.
How do I make the resolution bigger?
System > Screen Resolution only gives me 2 option:
640 X 480 
or 800X600

---

### Post by niyonk on 2008-07-23
Hiya, Pika :)

Try and see if there are any back-up files in the X11 folder ;) 
EDIT: the X11 folder is in /etc 
If you find any replace them with the original one (i think xorg.conf)

or try sudo displayconfig-gtk to configure your monitor

Or I can give you my back-up file if you have an nvidia card

---

### Post by WRDN on 2008-07-23
First, what graphics card are you using? You should install the latest driver for them.
When it boots and says running in low graphics mode, click configure, and then select the resolution you want for the monitor from the "Model" drop-down.

---

### Post by pikabuntu on 2008-07-23
where is the x11 folder?

---

### Post by northern lights on 2008-07-23
First, let's backup your current xorg.conf```
cp /etc/X11/xorg.conf /etc/X11/xorg.backup
```

Now, let's reconfigure the xserver:

Run ```
sudo /etc/init.d/gdm stop
``` from a terminal. You will be leaving the graphical environment, so remember the next two steps!

Press Alt+F1 to log in and execute ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Then restart the interface with ```
sudo /etc/init.d/gdm start
```

Try to change resolution again.

In case something gets (even more) screwed, revert back with```
cp /etc/X11/xorg.backup /etc/X11/xorg.conf
```

---

### Post by niyonk on 2008-07-23
> **pikabuntu said:**
> where is the x11 folder?

I slightly edited the post ;)

---

### Post by pikabuntu on 2008-07-23
> **northern lights said:**
> First, let's backup your current xorg.conf```
cp /etc/X11/xorg.conf /etc/X11/xorg.backup
```Now, let's reconfigure the xserver:

Run ```
sudo /etc/init.d/gdm stop
``` from a terminal. You will be leaving the graphical environment, so remember the next two steps!

Press Alt+F1 to log in and execute ```
sudo dpkg-reconfigure -phigh xserver-xorg
```Then restart the interface with ```
sudo /etc/init.d/gdm start
```Try to change resolution again.

In case something gets (even more) screwed, revert back with```
cp /etc/X11/xorg.backup /etc/X11/xorg.conf
```

ok here it goes!

---

### Post by pikabuntu on 2008-07-23
it worked!
thanks everyone

---

