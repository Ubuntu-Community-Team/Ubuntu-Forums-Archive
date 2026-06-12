---
title: "No exec line in session file xfce4 after upgrade to 9.04"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by dgerwin11 on 2009-04-26
When I turn on my computer I get this message:

no exec line in the session file: xfce4.
running the GNOME failsafe session instead

I click OK then it pops up to tell me I will start without start up scripts and to use the session to fix the problem.

How do I fix the problem?

---

### Post by henrik_daver on 2009-04-26
Check this: [https://bugs.launchpad.net/ubuntu/+source/xfce4-utils/+bug/354204]("https://bugs.launchpad.net/ubuntu/+source/xfce4-utils/+bug/354204"). For me, the change from "xfce4" to "xfce" in $HOME/.dmrc worked, but other solutions (to other problems with the same error message) have been found.

---

### Post by dgerwin11 on 2009-04-27
How do I find $HOME/.smrc ?

---

### Post by zerebruin on 2009-04-29
> **dgerwin11 said:**
> How do I find $HOME/.smrc ?

in a terminal type 
```
sudo vi $HOME/.dmrc
```or, if you prefer another editor replace vi with that editors name (e.g. nano)


Changing xfce4 to xfce worked fine for me.

---

### Post by dgerwin11 on 2009-04-29
Thanks for getting me to $HOME/.dmrc  Unfortunately replacing xfce4 with xfce did not work for me.  Guess I'll have to  keep using the failsafe mode til the bug is fixed.

---

### Post by alpho2k on 2009-05-03
thanks, it worked for me!

---

### Post by dgerwin11 on 2009-05-04
how did you do it?  I can type in the new line, but when I hit enter, nothing happens

---

### Post by jimbob83 on 2009-05-25
I had the same problem after upgrading from 8.10.  I couldn't find any $HOME/.dmrc file, so I copied bcasanov's file from the link above, changed xfce4 to xfce and now it boots to the desktop.

---

