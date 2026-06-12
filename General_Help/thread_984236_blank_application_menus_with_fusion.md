---
title: "blank application menus with fusion"
date: 2008-11-16
forum: General Help
---

### Post by mfaust731 on 2008-11-16
Hey guys,
I need some help, please.
I have Ibex running with the nvidia ver.96 proprietary drivers enabled.
Fusion works fine, however when fusion is running certain applications will not display any text on their menu's, I get the icons but nothing else.
It is only a few apps that have issues, Scribus is one and Google earth is another.
Never had this happen before, any ideas?

---

### Post by binbash on 2008-11-16
this is talked a lot here.This is also a bug report @ openoffice bugzilla.

EDIT : I didnt see any solution to this @bugzilla @ubuntuforums.BUt i may miss some threads.

---

### Post by mfaust731 on 2008-11-16
ok, I didn't see any relevent posts
Open office works fine, is there a fix?

---

### Post by mfaust731 on 2008-11-17
So is the only fix , go back to hardy?
I see no anwsers here

---

### Post by IceReaver75 on 2008-11-17
If you are using a Geforce 6xxx or 7xxxx series card you can downloaded the new 180.06 beta drivers from Nvidias website.  You have to install them manually but it will take care of all your window and blank application menu problems.  Even though they are beta drivers I have been using them for 2 days now and haven't seen any problems at all with my system.  With the 177 drivers I was getting the title bar flickers and with the 96 drivers the title bar flicker went away but was getting the blank application menus now I have neither.  So it worth giving a try.

---

### Post by dan.s.ward on 2008-12-21
I was having the same problem with a NVidia Geforce4Go.

Enabling subpixel rendering fixed it for me.
System Settings -> Appearance -> Fonts: Enabled
Configure -> Use sub-pixel rendering: Enabled

Found the suggestion here:
[http://ubuntuforums.org/showthread.php?t=977745&highlight=blank+menus&page=3]("http://ubuntuforums.org/showthread.php?t=977745&highlight=blank+menus&page=3")

---

