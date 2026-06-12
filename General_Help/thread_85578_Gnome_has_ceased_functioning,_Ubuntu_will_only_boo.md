---
title: "Gnome has ceased functioning, Ubuntu will only boot into text-only mode."
date: 2005-11-03
forum: General Help
---

### Post by Plank117 on 2005-11-03
Gnome went on the fritz today while I was trying to get my wifi card working. I was installing kde-base but then aborted it. Apparently it unistalled gnome, so now I have no GUI. I tried apt-get ubuntu-base, apt-get ubuntu-desktop (which returned dependency errors) and apt-get gnome-desktop. None of these things have worked. I have rebooted several times, but I still get the same text-only login prompt. How do I fix this? Will I have to do a complete reinstall? It looks like I've got all the stuff I need for gnome, but the GUI still doesn't work. Any suggestions?

---

### Post by aysiu on 2005-11-03
What happens when you type this? ```
startx
``` or if you press control-alt-F7? What are the errors you get when you try to ```
sudo apt-get install ubuntu-desktop
```?

---

### Post by az on 2005-11-03
First 

sudo apt-get -f install

and follow any instructions (like dpkg --configure -a)

---

### Post by Plank117 on 2005-11-04
Okay, I tried startx and that didn't work. Apt-get install ubuntu-desktop returned dependency errors. However, I will try azz's suggestion and aysiu's key combination this weekend. Lots of work I have to get done right now. Thanks for your concern, may death come quickly to your enemies.
<edit>
Alright, I have now tried the following:
```

$ apt-get install ubuntu-base
$ apt-get install ubuntu-desktop (unmet dependencies)
$ apt-get -f install

```
I have also tried Ctrl-Alt-F7.

A note on apt-get -f install:
When I ran it, I received some errors. However, this may be due to the fact that I was not connected to the internet at the time. (I'm using a school computer right now.) However, these packages look promising, as they appear to be programs used for opening libraries.
</edit>

---

### Post by Plank117 on 2005-11-04
Okay, the problem with apt-get -f install was definitely the fact that I was not connected to the internet.

---

### Post by eyebrowman92 on 2005-11-08
i had the same problem before i upgraded to breezy. right after i got hoary (happened to be the same day i upgraded to breezy) i shut off my computer and restarted it. gnome never loaded up. so i figured ah what the hell so i reinstalled and without restarting upgraded to breezy and everything was fine.

---

### Post by Qrk on 2005-11-08
What errors did startx return?

---

