---
title: "How do I fix my screen resolution??"
date: 2008-11-05
forum: General Help
---

### Post by obiwaynekenobi on 2008-11-05
I accidentally set my screen resolution to something that isn't supported on my monitor, and now I get a blank screen that says the resolution is not supported.

How the heck do I fix this?  On Windows it would just reset to the old value.  I tried sudo dpkg-reconfigure -phigh xserver-xorg but nothing happened, and I can't get to the graphical interface to change the resolution back to what it should be!

My xorg.conf is empty (well not empty, but doesn't have anything saying the resolution that I set it to that's incompatible, so I can change it back), so I don't even know what its settings should be.  I didn't touch it at all when I set up 8.10.

Can anyone help me?  Something like this should be trivially simple, but it's not for some reason.

---

### Post by wgrant on 2008-11-05
Try removing ~/.config/monitors.xml. gnome-display-properties did originally ask you to confirm the new settings within 30 seconds, but that feature has apparently been lost somewhere along the line.

---

### Post by fooman on 2008-11-05
if you can boot into recovery mode...try the xfix option.

---

### Post by flameproof on 2008-11-05
I had exactly the same problem with 8.10 a few days ago.

[http://ubuntuforums.org/showthread.php?t=964689](http://ubuntuforums.org/showthread.php?t=964689)

My rescue was: 

Start up
get the black screen
ctrl+alt+F3
sudo dpkg-reconfigure -phigh xserver-xorg

Or did I do start > esc ?

Try it. But it is very annoying. Seems they didn't want to do that 20 Seconds try and change back to before as in Windows since Windows is seen as evil evil evil and no idea can be taken from it coz all is bad bad bad. Not my way of thinking.

---

### Post by obiwaynekenobi on 2008-11-05
Thanks.  Removing the monitors.xml file did the trick!

---

