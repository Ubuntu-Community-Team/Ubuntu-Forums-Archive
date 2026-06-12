---
title: "ATI video drivers on older machine"
date: 2008-09-17
forum: General Help
---

### Post by tone33 on 2008-09-17
I have a pentium II 400 Mhz w/ 256MB ram.  I know...  it's really old, trying to fix it up with Ubuntu for a neighbor.  so i did a command line install of 8.04.  Then installed Fluxbox and Firefox and i can start up the WM and get to the internet via Firefox - yay!  But it looks terrible.  How do I install drivers for this via command line?  It's an ATI video card w/3D...  probably 8 or 16MB.

---

### Post by jonian_g on 2008-09-17
Use envy to install the drivers. To install envy:
```
sudo apt-get install envyng-gtk
```
And then run it with:
```
envyng-gtk
```
and install the drivers from there.

---

### Post by tone33 on 2008-09-17
i did that... it ran through the install and said no drivers found for your card.  So i then selected 'manual' and it said 'proceed at your own risk' so i did - never having an option to choose a driver.  It finished doing whatever it was it was doing and then prompted me for a reboot.  Now I try to startx and get 

```

Fatal server error: 
no screens found
giving up.
xinit: Connection reset by peer (errno 104): unable to connect to X server
xinit: No such process (errno 3): Server error.

```

Can i reconfigure my x server through a tool?  Or do i need to look in the xorg.conf file and do something?  Any ideas?

---

### Post by jonian_g on 2008-09-17
You can restore the backed up xorg.conf:
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

You can try to config xorg automatically by typing:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by tone33 on 2008-09-17
ok got it back to default and i can startx again.  I do a lspci and get this for the card:

ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c).  Any idea if there is a driver available for this?  And how i could get it?

---

### Post by jonian_g on 2008-09-17
No idea, sorry. Hope someone else knows.

---

