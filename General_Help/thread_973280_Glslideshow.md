---
title: "Glslideshow"
date: 2008-11-06
forum: General Help
---

### Post by Valkyrio on 2008-11-06
Alright...I've been trying to figure out how to change the settings for glslideshow for a while and can't figure out how to. 

First I was told to modify glslideshow.desktop (which doesn't exist or I can't find.) Then I tried modifying the glslideshow.xml under usr/share/xscreensaver/config, but I'm not actually sure how to modify it (I tried modifying the labels, didn't do anything, so I modified the command arg using options given by the man pages and still nothing.)

Any help is greatly appreciated.

---

### Post by ajgreeny on 2008-11-06
This may or may not be what you are looking for, but here goes.

You can edit the folder used for the gnome-screensaver "Pictures Folder" by doing the following:-

Edit the Pictures folder configuration file:
```
sudo gedit /usr/share/applications/screensavers/personal-slideshow.desktop
```
Find the line
```
Exec=slideshow --location=Pictures
```
(In Hardy Heron, the line is simply "exec=slideshow" but I have no idea about Intrepid at the moment. To customize the location, just add "--location=PATH," where PATH is the location of your pictures, for example:-
Exec=slideshow --location=/path/to/your/Pictures_folder

I think there are other configuration choices that can be made regarding time between pictures etc etc, but I can't remember where I read that.

---

### Post by Valkyrio on 2008-11-07
Hm, I changed the location already by creating a .xscreensaver file in my home directory, but I was trying to change the pan and duration, etc.

I modified the Exec, as other sites say to...didn't work.

---

### Post by mdizzle on 2009-02-25
checking the man page for glslideshow says:

 To specify the directory that images are loaded from,
run xscreensaver-demo(1) and click on the "Advanced" tab.

---

