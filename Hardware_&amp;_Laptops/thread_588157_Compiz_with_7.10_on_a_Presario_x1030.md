---
title: "Compiz with 7.10 on a Presario x1030"
date: 2007-10-23
forum: Hardware &amp; Laptops
---

### Post by TheQuicksilver on 2007-10-23
Well, research seems to imply that this should work, running Compiz under a Radeon Mobility 9200.  But, when Gusty tries to start, after logging in, XServer restarts and kicks me back out to the login screen.  I can start Failsafe GNOME and it will run fine, without Compiz of course.

I would either like to figure out the right way to get Compiz running on my Presario X1030 with a Mobility 9200, or tell Ubuntu not to use Compiz so that I don't have to switch sessions to Failsafe every time that I log in.  The first time I logged in to failsafe, there was a bubble that popped up that said something to the effect of creating a particularly named file in a certain directory to disable Compiz, but I was troubleshooting at the time and didn't write down the instructions, now I can't track it down.

I have already turned Desktop Effects down to No Effects.

---

### Post by TheQuicksilver on 2007-10-23
Bump for any thoughts on the problem?

---

### Post by #Reistlehr- on 2007-10-23
try:

```

sudo apt-get remove compizconfig-settings-manager

```

If it's not installed, try to install it.

---

### Post by TheQuicksilver on 2007-10-23
It was uninstalled from my first round of trying to disable it.  Reinstalling it changes nothing, trying to log in under XGL instead of GNOME changes nothing.

---

### Post by TheQuicksilver on 2007-10-23
I also made sure my composite extension was installed.

---

### Post by #Reistlehr- on 2007-10-23
[http://ubuntuforums.org/showthread.php?t=588423](http://ubuntuforums.org/showthread.php?t=588423)

Read that thread. Might help some

---

### Post by TheQuicksilver on 2007-10-23
Just read that and followed the instructions in [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide).  No dice.  All it did was kill XServer completely and had to do a dpkg-reconfigure xserver-xorg to get the GUI back.  Afterwards, same issues as always.

---

### Post by TheQuicksilver on 2007-10-24
Is there a way to set metacity to be the default window manager instead of compiz?  That would do the trick don't you think?

---

### Post by TheQuicksilver on 2007-10-24
I'm really running on fumes over here for ideas.  Any suggestions I am happy to entertain.  From what I am reading, if there was a hardware conflict with the drivers, 7.10 should kick into BulletProof-X, but this does not happen.  All it does when I try to log into a normal GNOME session is kick me right back to the login screen, no explanation given.  Is there a log somewhere I can look at at least?

---

