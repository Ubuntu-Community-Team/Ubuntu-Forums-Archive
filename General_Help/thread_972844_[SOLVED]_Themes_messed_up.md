---
title: "[SOLVED] Themes messed up"
date: 2008-11-06
forum: General Help
---

### Post by sharat87 on 2008-11-06
Hello, I have been using the Dark themes that came along with the Intrepid... until I started trying other themes from gnome-look and installed a few.

I felt I installed too many themes and started deleting them from my .themes folder when I accidentally deleted two folders whose names started with .themes or .theme and continued with a few digits.

Now, I cant find both the dark theme I previously used and the default ubuntu human theme. Like that's not enough, whatever theme I apply other than the default gnome-themes like clear-looks and crux, they apply partially and give a message that some theme engine is not installed.

Please help, or I think I'll have to reinstall ubuntu :(

---

### Post by renzokuken on 2008-11-06
the engines are available in the repos and should fix the theme issues.

different themes use different engines such as the clearlooks engine and pixmaps engine.

fire up synaptic and searh for "engines", the theme engines are named **gtk2-*engines-name***

just tick the ones you want, e.g. crux, clearlooks, pixmap etc and install them, then try applying your themes again

---

### Post by sharat87 on 2008-11-06
Thanks for the response

I did that, I installed/reinstalled all the gtk-engines-*** packages, but the two missing themes still do not appear.

Any other ideas??

---

### Post by NilsE on 2008-11-06
You may still have to re-install the themes themselves since  they don't come with the engines.  Search for the ones you want in Synaptic such as darkroom but first re-install gnome-themes since it includes a couple of themes.

---

### Post by renzokuken on 2008-11-06
perhaps the themes got deleted???? are they still in your /home/.themes folder?

and it should be gtk**[color=red]2[/color]**-engines-**** that you installed.....note the 2

---

### Post by sharat87 on 2008-11-06
Yes, there are no themes in the folder ~/.themes

and ya... they were indeed gtk2-engines-***... just a typo, my bad.

I reinstalled gnome-themes package and searching for darkroom does not give any themes, it gives one package named 'darkroom' which is described as an 'immage' manipulation tool... am I missing something :confused:

---

### Post by renzokuken on 2008-11-06
have you checked the root theme folder?

have a look in /root/.themes

---

### Post by sharat87 on 2008-11-06
well, if the root theme folder's location is /root/.themes, then this folder does not exist...

---

### Post by renzokuken on 2008-11-06
ok, well i have just read that renaming the .themes folder in you home directory and restarting X may solve the problem by generating a new one.

rename the folder to something like .themes_backup, then hit Ctrl+Alt+Bckspace to restart X........log back in.....

if it doesnt work and you get no GUI then use a TTY to restore the folder back to how it was and run

```
startx
```

---

### Post by sharat87 on 2008-11-06
ok, i'll try that and be back in 5 mins :)
hope this one works

---

### Post by renzokuken on 2008-11-06
if that doesnt try just installing the following

```
sudo apt-get install ubuntu-artwork
```

---

### Post by sharat87 on 2008-11-06
I renamed the .themes folder and hit the hotkey... and the login window appeared just like always and I logged in... but it did not create a new .themes folder...

this is driving me crazeeeeee!!!

---

### Post by sharat87 on 2008-11-06
> **renzokuken said:**
> if that doesnt try just installing the following

```
sudo apt-get install ubuntu-artwork
```
cool beans!! that just worked!!! looooooolll

Thank you very very much renzokuken

btw, how do I mark this thread solved and how do I thank you??? am new to these forums :P

---

### Post by renzokuken on 2008-11-06
lol, congrats on solving your problem. personally i have no idea how to mark it solved, but to thank just click on the medal icon in the bottom right of my post

EDIT: looks like you figured it out anyway.....happy ubuntuing

---

### Post by sharat87 on 2008-11-06
ya, I figured that out... and to mark the thread solved, I  found the proper option in the Thread Tools menu/link on the top right of the page.

Thanks again :)

---

