---
title: "Wacom Bamboo compatibility?"
date: 2010-12-26
forum: Hardware
---

### Post by SchizmWolf on 2010-12-26
Hey all,
I'm thinking about buying a Wacom Bamboo Touch Tablet for arting purposes, but my question is: will it work on my computer? Currently I'm running Kubuntu Jaunty (9.04) on a Toshiba Satellite laptop with 2gb RAM and a Radeon 7200 Family Series o/b graphics card. Will it be compatible? I know that most one-touch, plug-n-play style things tend to work, but I've had them NOT work as well, so I'd like to know before I make a purchase that won't even work for me. Thanks, and hope for some feedback soon!:D

---

### Post by Favux on 2010-12-26
Hi SchizmWolf,

Yes.  You would have to compile linuxwacom 0.8.8-10 as the default wacom.ko (the usb kernel driver) doesn't support your model and to get multitouch features.  So you could follow I. in the [Bamboo P & T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1") except you would do a 'sudo make install' at the end before doing the copy command.  You would skip the cloning xf86-input-wacom since you're in Jaunty.  Then you need a modified .fdi, see:  [http://ubuntuforums.org/showpost.php?p=8165182&postcount=384](http://ubuntuforums.org/showpost.php?p=8165182&postcount=384)  Although with the newer wacomcpl you don't need the lines that turn output into stylus, touch, eraser, and pad.

---

### Post by SchizmWolf on 2010-12-26
Thanks for the prompt response! It's a little bit involved for my taste, but I think I'll be able to get it up and running with the how-to.  Just to be safe, there's not going to be any interference from using KDE4 will there? I just noticed that the how-to uses a lot of Gnome nomenclature is all.

---

### Post by Favux on 2010-12-26
Shouldn't be a big deal.  You'd have to make a few minor changes to account for KDE.  Mainly downloading and compiling on the Desktop if you don't have that desktop widget.  And I think autostart for the script is a little different.

---

