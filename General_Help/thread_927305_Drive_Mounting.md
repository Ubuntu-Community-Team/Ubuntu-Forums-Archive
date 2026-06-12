---
title: "Drive Mounting"
date: 2008-09-22
forum: General Help
---

### Post by FLCL on 2008-09-22
I have a hard drive dedicated to space, which holds my music and other things, so whenever i want to listen to music, i just mount the drive. 

As of just recently though, it starting mounting differently. It used to just mount and show the drive on my desktop, but now whenever i click the drive to mount it, the entire drive opens up upon mounting. This started happening after i installed Banshee, and gtkpod. 

I fully uninstalled banshee but it still does it, and havnt tried gtkpod yet. It's sorta annoying, does anyone know why it's opening upon mount, and how i can make it stop? Help is greatly appreciated :(

---

### Post by mc4man on 2008-09-22
I've always seen 4 ways to mount drives with the mouse. Two will mount and display, two will mount only.
Mount and display  
double left click in 'computer'  
single left click from 'Places' *in top panel* (or "Places -  Removable Media' if you have a lot of drives, partitions

Mount only 
right click - mount in 'computer' 
single left click from 'Places' when *in a file browse*r. (a second left click will display



There are loads of settings in the configuration editor - some have effect, a lot don't

---

### Post by FLCL on 2008-09-22
Thats the problem, it used to only mount when i single left click from 'Places' area in the top bar, but now it mounts and displays. Both(single) right clicking and left clicking mount and display.

---

### Post by mc4man on 2008-09-22
I've never seen it any other way, but maybe it was different.  ?

Do you have a places in the file browser window?

you can look thru here but I didn't see anything (and a lot of setting have no effect

> gconf-editor

---

### Post by FLCL on 2008-09-22
It used to never open upon mount. When im in the file browser and i left click it once, it mounts only though, but not if i do it through the 'Places' area. It's strange. 
I'll try looking through it, and post back if i get any results

---

### Post by FLCL on 2008-09-23
Well in the volume manager settings, autobrowse isnt checked, but I don't think it registers the hdd as an external media device. So I'm not sure, anyone else have any input? x.x;

---

### Post by RobOrr on 2008-09-23
I have a second harddrive for music and so forth - I ended up just setting it to automatically mount as it annoyed me that whenever i forgot to mount before playing music I would get a tremendous whinging rant from Rhythmbox. 

If automounting would be helpful check out fstab:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Was useful to me!

---

