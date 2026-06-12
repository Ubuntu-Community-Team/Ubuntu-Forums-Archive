---
title: "[SOLVED] Wallpaper goes off on reboot"
date: 2008-09-25
forum: General Help
---

### Post by YldGuy on 2008-09-25
My desktop wallpaper doesn't stay. It goes off when i reboot my PC and replaces it with the default heron wallpaper which i had earlier. Also, the terminal launcher i put on the panel also goes away. I am not sure if this is happening after i moved my home to a different partition but it looks so. I haven't tried changing my wallpapers earlier so I don't know how was the case earlier too. Any ideas why this might be happening?

---

### Post by ozorba on 2008-09-26
> **YldGuy said:**
> My desktop wallpaper doesn't stay. It goes off when i reboot my PC and replaces it with the default heron wallpaper which i had earlier. Also, the terminal launcher i put on the panel also goes away. I am not sure if this is happening after i moved my home to a different partition but it looks so. I haven't tried changing my wallpapers earlier so I don't know how was the case earlier too. Any ideas why this might be happening?

Your customised wall paper is in the following file in your home directory.

.gnome2/backgrounds.xml 

Check if you have this file.

---

### Post by YldGuy on 2008-09-26
> **ozorba said:**
> Your customised wall paper is in the following file in your home directory.

.gnome2/backgrounds.xml 

Check if you have this file.

its there. i opened it and saw my current wallpaper along with the hardy heron. have to reboot and see if it changes again now.

---

### Post by anotherdisciple on 2008-09-26
This is going to sound weird, but just try it for me....


Set your wallpaper and make the launcher for the terminal, then log out. Log back in and then restart.

Sometimes when things aren't shutting down properly it will lose your settings. However, it saves your settings every time you log out, so that should solve the problem.

---

### Post by YldGuy on 2008-09-27
> **anotherdisciple said:**
> This is going to sound weird, but just try it for me....


Set your wallpaper and make the launcher for the terminal, then log out. Log back in and then restart.

Sometimes when things aren't shutting down properly it will lose your settings. However, it saves your settings every time you log out, so that should solve the problem.


i changed the wallpaper...put the terminal in the panel .. logged off and logged back in. there it was.. the heron and the terminal was gone from the panel... the text file which i had put on desktop was still there.. i guess its something to do with the authority somewhere... some of the folders were mysteriously defaulted to root authority in home folder when i moved it to a different partition. had to go and set them to my username manually for skype and many other apps.. i suspect something related to desktop settings are still locked to root.. any directory path i can go in and take a look in home?

---

### Post by YldGuy on 2008-09-27
hi all... just fixed this stupid thing.. remember, i said i had moved my home to diff partition and most of the folders are owned by root.. i figured its not getting proper authority to commit changes. was going to change owner manually but looked at so many folders and subfolders and subfolders and subfolders and... you get the idea.. :) .. and decided to do it via chown after few minutes of research in the forum. ran this in terminal "chown -R uname /home/uname" and i am all good to go.. wallpaper stayed, terminal is in panel. i am good to go. thanks all for replying.

---

