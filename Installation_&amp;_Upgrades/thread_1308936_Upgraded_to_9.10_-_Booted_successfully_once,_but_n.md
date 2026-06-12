---
title: "Upgraded to 9.10 - Booted successfully once, but now just loads command prompt"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by bbiggers on 2009-11-01
Like the title says, I upgraded to 9.10 without any trouble, and managed to boot it up once, but now every time I reboot, right after I get the little white ubuntu symbol, it gives me a text-only login screen, and after I log in it just gives me the command prompt.  I'm far from being a power user, and not particularly handy with the command prompt, so...

Is there a command I can type in that will get me into gnome?

Better yet, is there something I can do so that I'll get the graphical login screen and not end up just in command prompt?

Or should I just cut my losses and go for a clean install?

Thanks for any help you can provide, I know everyone is busy with their own upgrades and installs right now.

---

### Post by bashphoenux on 2009-11-01
did you change the type of login session????
try ctrl+alt+f7 and see if the GUI login is available ... if so at the bottom change the type of session to gnome !!

---

### Post by Sunflower1970 on 2009-11-01
I had a similar problem. I'm using an nVidia 7600 GT card for graphics. What I had to do to get to the desktop is this:

1. log in at command prompt
2. edit the xorg.conf like so: 
```
sudo nano /etc/X11/xorg.conf
```
3. look for a section that will say something like this: 
```
Section "Device"
	Identifier	"Default Device"
	Driver	"the driver here"
	Option	"NoLogo"	"True"
EndSection
```
4. Change the Driver to vesa
5. To save in nano, Ctrl+X, then when prompted to Save, hit the 'Y', then hit enter.
6. Reboot
7. Hopefully this will get you to the desktop to do updates, and get a driver for your video card. 

I've installed the restricted drivers for my card, but haven't rebooted yet to make sure they work

---

