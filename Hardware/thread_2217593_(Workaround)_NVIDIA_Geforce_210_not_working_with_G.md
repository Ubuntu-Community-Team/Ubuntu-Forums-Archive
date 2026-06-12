---
title: "(Workaround) NVIDIA Geforce 210 not working with Gnome &quot;flavor&quot;"
date: 2014-04-18
forum: Hardware
---

### Post by chesaro on 2014-04-18
I installed the ubuntu (Unity) 14.04 on the morning, the driver worked just fine, and realized i couldn't change desktops directly, so i started to look around the web, but nothing. On a google result, i found out there was an Ubuntu version with Gnome by default (ubuntugnome.org), so i just decided to cut the Unity garbage and install it, for my deception the version just didn't work like the Unity version, after i installed the nvidia driver, the loading window just freezed. After a couple tries, i could make it enter the login window (made it installing ligthdm and making it the default manager), but, again, i couldn't login, it was very frustating so i decided to go back (meanwhile) to the Unity version, does anybody knows a workaround, fix or anything about this?

[B]Edit
[/B]I'm not very sure, but i think the problem is directly related to the gdm manager.
Also, it was very dificult (i had to enter recovery mode) to stop gdm, it just went black after a 'sudo service gdm stop' command on the command line (after a Ctrl+Alt+F1) instead of just stopping like lightdm

---

### Post by 23dornot23d on 2014-04-18
I would go back to the one that worked properly and then just install gnome-shell

> 
I installed the ubuntu (Unity) 14.04 on the morning, the driver worked  just fine, and realized i couldn't change desktops directly,


[B]sudo apt-get update
sudo apt-get install aptitude
sudo aptitude update
sudo aptitude install gnome-shell
sudo aptitude install gnome-tweak-tool
[/B]
____________________________________________

or if you want to try in the one you are now in .........

[B]sudo apt-get update
sudo apt-get install lightdm[/B]

if that is not working - I always just switch across to kdm

[B]sudo apt-get update
sudo apt-get install kdm[/B]

kdm rarely ever fails me ........ but lightdm and gdm ...... seem slightly more temperamental sometimes.

---

### Post by chesaro on 2014-04-18
> **23dornot23d said:**
> 
[B]sudo apt-get update
sudo apt-get install lightdm[/B]


Actually i tried that, but i only got as far as the login window, but i've tried again with the Unity version, and finally changed the desktop, i didn't know the ubuntu-gnome-desktop package was added to configure and add (or something like that) the gnome-* desktop to the list displayed on the login window, sorry to said it until now, but i just upgraded from 12.04 and missed some things that was added/changed during the 12.10/13.04/13.10 cycles to the ubuntu environment, but thanks anyway

---

