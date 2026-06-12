---
title: "gnome, kubuntu, and icons"
date: 2005-12-04
forum: General Help
---

### Post by drotter on 2005-12-04
I orginally installed kubuntu on my computer with out any problems.  But since the computer im using is kind of old (pIII w/ 265 ram) I decided to try gnome because i figured it would use less resouces.  I installed gnome with apt-get install gnome-desktop and installed it with no problems.

Here's the question.  I like gnome...better then kde.  Could I uninstall kde now with out any problems (apt-get blah blah).  Will being orginally configured for KDE screw up X server when you get rid of it?

Another point...I notice that the preformance of gnome changes signficiantly depending on the theme and icons i use.  Am i making this up or has other people noticed it?

thanks for the help

---

### Post by aysiu on 2005-12-04
[QUOTE=drotter]I orginally installed kubuntu on my computer with out any problems.  But since the computer im using is kind of old (pIII w/ 265 ram) I decided to try gnome because i figured it would use less resouces.  I installed gnome with apt-get install gnome-desktop and installed it with no problems.[/quote] 256 MB of RAM should be just fine. If you want a super lightweight desktop environment, try XFCE (sudo apt-get install xubuntu-desktop).

> 
Here's the question.  I like gnome...better then kde.  Could I uninstall kde now with out any problems (apt-get blah blah).  Will being orginally configured for KDE screw up X server when you get rid of it? I made [a HowTo on this.](http://www.ubuntuforums.org/showthread.php?t=96048)

> 
Another point...I notice that the preformance of gnome changes signficiantly depending on the theme and icons i use.  Am i making this up or has other people noticed it? I've noticed this, too. I have a great controls theme called RPanther, but I can't use it because it's too slow.

---

### Post by silex on 2005-12-04
Uninstalling KDE won't damage your X server or anything like that because they're separate systems due to the wonders of linux :D .  The problem with uninstalling KDE is that you have to go through and uninstall all the parts.  Probably the easiest way to do this is to use Synaptic (GNOME's graphical frontend for apt-get) and search for QT and the base KDE system and uninstall those.  All the other KDE packages depend on these, and will be uninstalled as well.

P.S. - If you're worried about your windowmanager eating up too much resources, look into installing XFCE.  Its even lighter weight than GNOME.

---

### Post by aysiu on 2005-12-04
[QUOTE=silex]Uninstalling KDE won't damage your X server or anything like that because they're separate systems due to the wonders of linux :D .  The problem with uninstalling KDE is that you have to go through and uninstall all the parts.  Probably the easiest way to do this is to use Synaptic (GNOME's graphical frontend for apt-get) and search for QT and the base KDE system and uninstall those.  All the other KDE packages depend on these, and will be uninstalled as well.[/QUOTE] Or you could use the HowTo I linked to earlier, which is even easier--copy and paste.

---

