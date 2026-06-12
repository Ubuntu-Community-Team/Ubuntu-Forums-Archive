---
title: "Black Screen/ GUI Missing"
date: 2008-01-19
forum: Hardware &amp; Laptops
---

### Post by teejay17 on 2008-01-19
Yes, when I do a fresh installation of any variation of 7.10 (Flux,X,K, Ubuntu) my screen goes totally blank after the short little splash animation. Basically, there's some squiggly lines, then nothing. Again, that goes for all flavours.
My only work around so far has been to install 7.04, then do an upgrade from it. There's got to be a better way. 
Does anyone know why I might be having this problem? More importantly, does anyone know how I can fix it? 
Currently, I have Fluxbuntu installed, but that shouldn't make a difference seeing as it affects every one equally. 
Thanks in advance.

---

### Post by bethebunny on 2008-01-19
Most likely your graphics drivers are not working. The first thing I would try would be Ctrl+Alt+F1. If that gets you to a command line, then it is very definitely your graphics drivers. Log in and do

dpkg-reconfigure -phigh xserver-xorg

This should reset your xorg.conf file to a default that will work with your graphics card. Restart your computer and it should boot into a gui (alternatively you could kill xserver and gdm and restart them, but rebooting is generally less bothersome).

Hope this helps.

---

### Post by teejay17 on 2008-01-19
> **bethebunny said:**
> Most likely your graphics drivers are not working. The first thing I would try would be Ctrl+Alt+F1. If that gets you to a command line, then it is very definitely your graphics drivers. Log in and do

dpkg-reconfigure -phigh xserver-xorg

This should reset your xorg.conf file to a default that will work with your graphics card. Restart your computer and it should boot into a gui (alternatively you could kill xserver and gdm and restart them, but rebooting is generally less bothersome).

Hope this helps.
Okay, thanks. I'll see if that works.

---

### Post by teejay17 on 2008-01-19
> **bethebunny said:**
> Most likely your graphics drivers are not working. The first thing I would try would be Ctrl+Alt+F1. If that gets you to a command line, then it is very definitely your graphics drivers. Log in and do

dpkg-reconfigure -phigh xserver-xorg

This should reset your xorg.conf file to a default that will work with your graphics card. Restart your computer and it should boot into a gui (alternatively you could kill xserver and gdm and restart them, but rebooting is generally less bothersome).

Hope this helps.
It tells me that this "command is not found."

---

### Post by teejay17 on 2008-01-19
I did do the following though:
```

sudo dpkg-reconfigure xserver-xorg
```
but to no avail. After I went through the whole process, selecting the right resolution for my monitor, etc., my screen is still blank.

---

### Post by teejay17 on 2008-01-20
Bump. Someone must know what to do....

---

### Post by teejay17 on 2008-01-20
> **bethebunny said:**
> Most likely your graphics drivers are not working. The first thing I would try would be Ctrl+Alt+F1. If that gets you to a command line, then it is very definitely your graphics drivers. Log in and do

dpkg-reconfigure -phigh xserver-xorg

This should reset your xorg.conf file to a default that will work with your graphics card. Restart your computer and it should boot into a gui (alternatively you could kill xserver and gdm and restart them, but rebooting is generally less bothersome).

Hope this helps.
Ctrl+Alt+F1 doesn't get me a command line screen when it's in this state either.

---

### Post by teejay17 on 2008-01-20
The more I tinker with this, the more I see it being a xorg problem. 
I did a basic command-line installation, and everything was working fine until I installed xorg. After that, I again lost my display. 
What can I do to get the display working on my computer?

---

