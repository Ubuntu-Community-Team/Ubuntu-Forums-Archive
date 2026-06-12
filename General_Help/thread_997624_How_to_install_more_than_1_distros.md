---
title: "How to install more than 1 distros ?"
date: 2008-11-30
forum: General Help
---

### Post by rams123 on 2008-11-30
I have ubuntu 8.10 on pc. But when I'm trying to install other (Kubuntu) through Wubi it's showing uninstall ubuntu option. What to do ?

---

### Post by Swagman on 2008-11-30
Dont uninstall ubuntu.

If you want the kde desktop just open up a terminal and enter.....

```
 sudo apt-get install kubuntu-desktop
```

If you don't like using the terminal then go the long winded way by going into 

System > administration > synaptic

and enter kubuntu desktop in the search field.  Tick the little box next to kubuntu-desktop  and click apply.

[IMG]http://i261.photobucket.com/albums/ii45/Outcast_Aussie/terminalkde.jpg[/IMG]

Long winded way of doing sudo apt-get install kubuntu-desktop isn't it.

The terminal can be found in......

Applications > Accessories > Terminal

---

### Post by rams123 on 2008-11-30
Thanks Swagman. Does anyone know what's the size of kubuntu desktop. I have slow connection...

---

### Post by PGHammer on 2008-12-02
> **Swagman said:**
> Dont uninstall ubuntu.

If you want the kde desktop just open up a terminal and enter.....

```
 sudo apt-get install kubuntu-desktop
```

If you don't like using the terminal then go the long winded way by going into 

System > administration > synaptic

and enter kubuntu desktop in the search field.  Tick the little box next to kubuntu-desktop  and click apply.

[IMG]http://i261.photobucket.com/albums/ii45/Outcast_Aussie/terminalkde.jpg[/IMG]

Long winded way of doing sudo apt-get install kubuntu-desktop isn't it.

The terminal can be found in......

Applications > Accessories > Terminal

The terminal method is a bit quicker (I've used it to add Kubuntu to an existing Wubi-installed Ubuntu).

Why would a person want more than one 'buntu?

Simple, really; they use applications from more than one desktop (with the 'buntus, I normally like GNOME; however, there are some apps from KDE I prefer, or that have no GNOME equivalents, one example being KTorrent; also, there are times that I truly prefer KDE as a desktop).

---

### Post by Vadi on 2008-12-02
The lazy can just click [here]("apt:kubuntu-desktop").

---

