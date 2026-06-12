---
title: "Ubuntu GUI issue"
date: 2006-09-18
forum: Hardware &amp; Laptops
---

### Post by TwilightVampire on 2006-09-18
Hi all,

The other day I decided to dual boot Ubuntu and XP on my Sager 5320 laptop. Install seemed to go perfectly, but when I try to start Ubuntu, I cant get to a GUI. It is telling me that XServer isnt configured properly. Any ideas?

Computers specs are:

Pentium M 1.86Ghz
1.5GB RAM
80GB SATA HDD
ATI Radeon x700

I'm not exactly new to Linux but its very rare that I have to use just command line. I know most of the staple commands but I will probably need help with some of the more complex things.

Appriciate the help, ladies and gentlemen :)

---

### Post by bigken on 2006-09-18
Hi boot into recovery mode and type sudo dpkg-reconfigure xserver-xorg
the select your  graphics card and select your resolutions using the space bar ;)

---

### Post by TwilightVampire on 2006-09-18
I tried that and it didnt work. Exact same problem with no change.

The exact error is:

"Failed to start the X Server (Your Graphical Interface). It is likely that it is not setup correctly. Would you like to view the X server output to diagnose the problem?"

I tell it yes and it takes me to a rather short output and the only info beyond the basic is "Fatel server error: No screens found" 

I'm sure i've setup the screen and video card properly though.

---

### Post by bigken on 2006-09-18
ok run the comand again this time select vesa as your video driver

---

### Post by TwilightVampire on 2006-09-18
I dont remember it giving me an option to set vesa as my video driver. Where was that?

---

### Post by george_apan on 2006-09-18
Can you post the output of /var/log/Xorg.0.log ? At least have a look through it for anything that seems like an error with 'less /var/log/Xorg.0.log'.

---

### Post by TwilightVampire on 2006-09-18
> **bigken said:**
> ok run the comand again this time select vesa as your video driver

That worked! Thanks a lot :)

---

### Post by bigken on 2006-09-18
pleased to hear its working now look for a tutorial on how to install the correct  video drivers ;)

---

### Post by TwilightVampire on 2006-09-18
lol, thought I was originally. I chose the ATI drivers #-o

---

