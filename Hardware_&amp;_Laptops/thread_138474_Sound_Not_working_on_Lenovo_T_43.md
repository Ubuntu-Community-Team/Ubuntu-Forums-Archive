---
title: "Sound Not working on Lenovo T 43"
date: 2006-03-02
forum: Hardware &amp; Laptops
---

### Post by ramnarayan on 2006-03-02
Hi

I just installed (afresh) Ubuntu 5.10 Breezy on an IBM / Lenovo ThinkPad T43.

The previous OS was Ubuntu 5.04 on which sound was made to work with great difficulty. However, that too stopped working sometime soon after re-configuring some other stuff (don't remember what)

So is there anyone out here who has succesfully set up their T43 to play sound and video, easily.

By easily I mean without having to recompile the kernal, or compile a whole lot of drivers and other stuff.

I did some seraching and reading and found not so much to go by.

But here are the posts and other resources I checked out.

Sound posts:

[http://ubuntuforums.org/archive/index.php/t-75581.html](http://ubuntuforums.org/archive/index.php/t-75581.html)

[http://ubuntuforums.org/showthread.php?p=575727#post575727](http://ubuntuforums.org/showthread.php?p=575727#post575727)

Installing :

[http://www.columbia.edu/~em36/ubuntubreezythinkpadt42.html](http://www.columbia.edu/~em36/ubuntubreezythinkpadt42.html)

[http://sharadware.com/2005/06/13/installing-linux-on-the-ibm-thinkpad-t43/](http://sharadware.com/2005/06/13/installing-linux-on-the-ibm-thinkpad-t43/)

[http://www.cs.ust.hk/~joseph/Favorites/Debian/UbuntuOnIBMThinkpadT43.html](http://www.cs.ust.hk/~joseph/Favorites/Debian/UbuntuOnIBMThinkpadT43.html)

***

The machine belongs to my senior colleague who does not want to have too much downtime also my capabilities do not extend to extensive compiling and recompiling. 

regards
ram

---

### Post by whistl on 2006-03-13
I have working sound on my T43.  It worked initially, then it stopped, mysteriously.

I tried all kinds of things, even install alsa 1.0.11-rc3 drivers/lib/oss-lib/utils, with no improvement.

Then today, I pressed the hardware mute and volume up buttons (the little buttons just above F5), and bang, my audio is working again.  Ugh!

Now I don't know if upgrading the alsa drivers helped or not.  Maybe someone else can tell me if just pressing the hardware mute and/or volume up/down buttons solves the problem.

---

### Post by ramnarayan on 2006-03-16
[QUOTE=whistl]I have working sound on my T43.  It worked initially, then it stopped, mysteriously.

I tried all kinds of things, even install alsa 1.0.11-rc3 drivers/lib/oss-lib/utils, with no improvement.

Then today, I pressed the hardware mute and volume up buttons (the little buttons just above F5), and bang, my audio is working again.  Ugh!

Now I don't know if upgrading the alsa drivers helped or not.  Maybe someone else can tell me if just pressing the hardware mute and/or volume up/down buttons solves the problem.[/QUOTE]

wow - genius and its the buttons that did the trick . A BIG THANKS.  I did not have to reinstall anything - following your mail i was able to get sound woking very easily

thanks once again
ram

---

