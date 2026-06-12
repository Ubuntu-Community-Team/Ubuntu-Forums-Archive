---
title: "lxinput will not adjust"
date: 2011-04-30
forum: Hardware
---

### Post by arkanabar on 2011-04-30
I upgraded lubuntu from 10.10 to 11.04 and my mouse pointer lost its acceleration.  So I go menu > Settings > Keyboard and Mouse to activate lxinput, which manages settings for keyboard and mouse for LXDE.  But I can't adjust anything; if I move any of the sliders, any amount, with either keyboard or mouse, it closes.  Running it in terminal, I find it closes with a segmentation fault.  Is there a fix or alternate GTK mouse configuring utility I can use?

---

### Post by arkanabar on 2011-04-30
bug already noted, [https://bugs.launchpad.net/ubuntu/+source/lxinput/+bug/725194](https://bugs.launchpad.net/ubuntu/+source/lxinput/+bug/725194)

I'd still like an alternative if one can be found.   gpointing-device-settings does not adjust acceleration, and gsynaptics is a metapackage that points to gpointing-device-settings.

---

### Post by Black_Parrot on 2011-06-02
I have the same problem does anyone have solved this?

Asus eee1005ha


---
I try gnome-mouse-properties and it looks like it work...

---

### Post by arkanabar on 2011-07-24
it's possible to do with xset.  the command (which works from the run dialog, alt-f2) would be something like ```
xset m N1 N2
``` where N1 is the amount of acceleration you want (I use either 2 or 5/2 for this value) and N2 is the number of pixels you move before it kicks in (I use 0).  This is desktop-independent, by the way.

Now what I want is to set things up so that this command is run when I log in.

---

### Post by andypag on 2012-01-02
there&#347; a file you can edit these settings directly. It only takes effect after a reboot.

And as I&#472;ve just discovered if you go into standby and then come out of it your back to square one until you reboot. 

Problem is I cant remember the file to edit and cant find the posting where I read it. Ubuntuquestions I think

---

