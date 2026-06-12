---
title: "[SOLVED] gnome won't start"
date: 2008-08-04
forum: General Help
---

### Post by unebaguettesvp on 2008-08-04
i screwed up gnome so bad. i was removing pulseaudio and related packages, which worked 100% flawlessly on another computer. so, i tried it on my work laptop. when i restarted, the only thing that i could see was my desktop wallpaper and awn. i could execute some programs. but i couldn't get a terminal, gedit, etc to work. gnome-panel didn't show up either. then i tried removing my gnome settings:

rm -rf .gnome .gnome2 .gconf .gconfd .metacity

that sort of worked. a gnome panel showed up. everything was back to a fresh install. but then it stalls! a window pops up saying it cant find a fast user switch applet. so then i press delete. and nothing happens! i can right click on some applets in my notification area.

any ideas? reinstalling ubuntu is not an option for me! any help would be appreciated! thanks!

---

### Post by ibuclaw on 2008-08-04
The only suggestion I can think of is to remove all .hidden directories and files except for:
[LIST]
[*]**.bash_logout**
[*]**.bashrc**
[*]**.profile**
[/LIST]
That would reset everything back to its factories though, and you'll have to setup awn/gnome/firefox/etc again...

[EDIT]
Actually, you can keep the .mozilla directory, along with any other directory that you can associate familiarity with too.

Regards
Iain

---

### Post by unebaguettesvp on 2008-08-04
i did that and still the same thing is happening.

i can click on items on the desktop. i have folders on the desktop, so when i double click. nautilus pops up and i can view whats inside but i can't go to other folders. i can now view the gnome panels but i can't click on them.

i tried dpkg-reconfigure xserver-xorg but that didn't work either.

any other ideas?

---

### Post by unebaguettesvp on 2008-08-04
my problem was esound. if i removed pulseaudio-esound-compat and replaced it with esound, that's what was causing the error. so, i removed esound completely and it seems to be working. although i wish i knew that before i deleted all my gnome settings! ](*,)

---

