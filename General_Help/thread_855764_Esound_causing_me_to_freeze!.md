---
title: "Esound causing me to freeze!"
date: 2008-07-10
forum: General Help
---

### Post by Chris077 on 2008-07-10
My initial problem was that my custom logout sound was not playing when I logged out of Ubuntu, so I searched the forums for similar problem. In one of the threads someone said to install the esound package. The thread's creator replied that that worked, so I myself installed the esound package by:

```
sudo apt-get install esound
```

It installed, so when I logged out and restarted it did not fix the problem. Now my problem is even worse! When I log in and try to launch any program (Terminal, Firefox, Appearance Preferences), all of Ubuntu freezes up. Before I installed esound and restarted, I had no problems. 

Is there a way to uninstall the esound package? (Remember that I cannot access the terminal when Ubuntu is loaded otherwise it will freeze before the window even pops-up.

I am running v8.04 of ubuntu.

Your help is greatly appreciated!

---

### Post by Chris077 on 2008-07-10
My problem has been solved! I entered Recovery Mode and removed it through there using:

```
sudo apt-get remove esound
```

---

### Post by unebaguettesvp on 2008-08-04
i am having this same problem too!! does anyone have any ideas? i uninstalled pulseaudio so installing pulseaudio-esound-compat is not an option. i would like to have system sounds too. anyone know what to do?

---

### Post by unebaguettesvp on 2008-08-08
fixed my problem with esound!

```
sudo gedit /etc/esound/esd.conf
```

change auto-spawn from 0 to 1. then restart.

hope that helps somebody!

---

### Post by dcstar on 2008-08-09
> **unebaguettesvp said:**
> fixed my problem with esound!

```
sudo gedit /etc/esound/esd.conf
```

change auto-spawn from 0 to 1. then restart.

hope that helps somebody!

Doesn't help on my 64 bit 8.04 system - with esound installed I get hang-ups and still no shutdown sound.

Must be something with the particular sound hardware some of us have....  L-(

---

