---
title: "I don't want to use AWN any more"
date: 2008-07-16
forum: General Help
---

### Post by the lemming on 2008-07-16
I installed AWN a month ago but I now want to stop using it but I don't know how to do this.

I have tried to remove everything relating to AWN in the Synaptic Package Manager.  I even tried to right click on the panel and choose close but then I re-boot I get AWN up and running again.

How do I get rid of it?

Cheers

---

### Post by pikabuntu on 2008-07-16
system>preferences >  awn manager
under the general tab, unclick  the "automatically start up awn on login" box

---

### Post by the lemming on 2008-07-16
> **pikabuntu said:**
> system>preferences >  awn manager
under the general tab, unclick  the "automatically start up awn on login" box


Sorry, but no such thing exists in the Preferences section.

---

### Post by pikabuntu on 2008-07-16
I know there is another way to do this... 
I will try to find it real quick for you.

---

### Post by rossjman1 on 2008-07-16
System, Preferences, Sessions, Uncheck Avant Window Navigator

sudo apt-get remove avant-window-navigator
OR
sudo apt-get remove avant-window-navigator-bzr
should work, though.

---

### Post by pikabuntu on 2008-07-16
you could try system>prefrences>sessions
this lets you configure what starts up when you log in

---

### Post by baju on 2008-07-16
You can also right-click on the awn bar and click "Dock Preferences" to see the dialog.

As far as I can remember was this feature introduced some months ago, maybe it's not in your version.

---

