---
title: "Different Background For Each Desktop"
date: 2008-09-13
forum: General Help
---

### Post by amj on 2008-09-13
I'm new to gnome & ubuntu, and can't find a setting for this, nor could I find it addressed here. 

I have 4 Workspaces set up.   I'd like to put a different desktop image on this, so that it's obvious which desktop I'm on. 

Is this possible?

Cheers, 
AJ

---

### Post by niteshifter on 2008-09-13
Hi,

Natively, as in some GNOME or Compiz setting? No. There is / was a third party app that did (wallpapoz, not in the repos) but I believe it's not actively maintained.

---

### Post by kokkus on 2008-09-13
You can use Drapes to have more then 1 wallpaper going random as your background, and therefor will also each workspace have different packgrounds.

---

### Post by Xgen on 2008-09-13
[http://anuragbansal.wordpress.com/2008/05/10/how-to-get-different-wallpapers-on-each-workspace-in-ubuntu/]("http://anuragbansal.wordpress.com/2008/05/10/how-to-get-different-wallpapers-on-each-workspace-in-ubuntu/")

---

### Post by Gondee on 2008-09-13
There is a way, but i have you warned that if you put a differnt background for each space you cant have icons on it, and the left and right click wont work on the desktop. 

But if you really want to:

you have to install compiz
```
sudo apt-get install compiz
```

Then open up synaptic and search compiz. you need to install advanced desktop effects settings. 
Then install compiz fuzion icon.

then open up the advanced desktop settings (system>preferences>advanced desktop settings. 

-Tick desktop cube
-Tick rotate cube

-Go to Desktop desktop cube>appearance> Select the pictures you want.



Open the compiz fuzion icon. (applications>system>compizfuzionicon)
It will appere in the bar in the top right click>window manager


1. ALT+F2
2. gconf-editor
3. Apps --> Nautilus --> Preferences
4. Untick "show desktop"

ctrl+alt+backspace

---

### Post by fooman on 2008-09-13
gondee,  i think the "advanced desktop settings manager" your referring to is actually "compizconfig-settings-manager" or ccsm.  it is in the repos, so can be installed with synaptic or in a terminal:

```
compizconfig-settings-manager
```

once its installed, open it in system > preferences > compizconfig settings manager.  when it opens, on the left, click "utility".  then on the right put a check next to "wallpaper" and double click the wallpaper icon.  when that opens, click the "new" button and navigate to the wallpaper you would like to add. click close.  then repeat for each side of your cube.

---

### Post by isecore on 2008-09-13
I've heard rumors (can't find a source for this though at the moment) that support for multiple-desktop wallpapers will be implemented in Nautilus within the not-too-distant future.

Hopefully this is true, since I find it a bit too dramatic sacrifice to kill off the desktop just to have multiple wallpapers.

---

