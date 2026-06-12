---
title: "help with installing AWN."
date: 2008-11-05
forum: General Help
---

### Post by bartre on 2008-11-05
hi, i'm trying to install AWN, but it's not quite working.
i'm following this guide for ubuntu 8.10
[http://ubuntuforums.org/showthread.php?t=762363](http://ubuntuforums.org/showthread.php?t=762363)
but when i put in the command "sudo tee -a /etc/apt/sources.list"
it doesn't do anything.
screen is what i'm talking about.

---

### Post by kestal on 2008-11-05
I think you may have made a bit of a mess of your sources.list. AWN should already be included (or at least mine was), in the repo. Have you just tried to sudo it to install? (thats what I did to get it to work when I tried it in 8.10). If not, do this:

go to terminal and type
> sudo gedit /etc/apt/sources.list

scroll down and find the lines you added (should be near the bottom) and remove them.

save/exit.

go to terminal again, and type

> sudo apt-get install avant-window-navigator

should work? maybe? (It did for me, almost out of the box at my point). If it wont work there, opening gedit through terminal and actually SEEING your sources.list is a bit easier than terminal-editing everything and making a mess of it. Gedit can be quite useful.

---

### Post by eternalnewbee on 2008-11-05
Main Menu > Add/Remove Applications. Type "avant" in tha searchbar. You'll get the one and only option: Avant Window navigator. Install. Aaa few seconds later, depending on your internet speed, after the installation is complete, go to: Main Menu > Accessories, and you'll find it somewhere at the top of the list.

---

### Post by bartre on 2008-11-05
sorry for the late reply i was in class.
okay, so i did the add/remove and searched for avant, i got a program simply labeled avant.  it shows up in my applications menu like in the first picture.
the problem comes in when i try to run that, i get an error, like in the second picture, any ideas?

---

### Post by ellalan on 2008-11-05
AWN is in synaptics, type awn in the search box. Tick "awn-applets-c-core" and click apply. Then you can start by going to Applications-> Accessories.
HTH.

---

### Post by bartre on 2008-11-05
thanks for your help guys, i figured it out, it was partially my list file, and i needed to use the add/remove, thanks again.

---

