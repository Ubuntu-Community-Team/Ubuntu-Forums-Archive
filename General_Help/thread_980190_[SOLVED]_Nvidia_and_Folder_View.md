---
title: "[SOLVED] Nvidia and Folder View"
date: 2008-11-12
forum: General Help
---

### Post by AlanR8 on 2008-11-12
Evening all

This Sony Vaio laptop has a Nvidia GeForce 8600M graphic card and all works well including Compiz. Nice and smooth.

However, if I try to put a "Folder View" widget on the desktop things grind to a halt. Processor usage goes up to 100% and eventually I can close the widget down and all is well again.

Now, I did come across this piece of wisdom in these forums that works. Paste into a terminal window the following:

> nvidia-settings -a InitialPixmapPlacement=2 -a GlyphCache=1


That done, I can add a "Folder View" and it's perfect. 

My question is, how do I make this command persistent between sessions. It seems that it looses it's effect on a reboot.

---

### Post by loomsen on 2008-11-12
System-->preferences-->sessions

and add the command just like it is :)

*edit*

missed you're running kde, 
[check this](http://itg.chem.indiana.edu/inc/wiki/software/168.html)

command is exactly the command you posted above

---

### Post by AlanR8 on 2008-11-12
Thanks Loomsen. Worked a treat.

---

### Post by Skripka on 2008-11-12
Excellent!! :KS


Has someone given a heads up to the KDE devs?  This was a big-one on my gripes list about Plasma.

Ods are to make it persistent, it needs to be run under a graphical sudo command....

---

### Post by Skripka on 2008-11-13
///bump///

Any indeas on loading that line on KDE load?  I tried a graphical sudo as well as addieing it to Autostart under "add a script"....any thoughts?

---

### Post by AlanR8 on 2008-11-14
Skripa

I just followed Loomsen's advice and clicked his link "check this". It took me to another page where it showed me exactly what to do.

It works a treat and I can now use Folder View perfectly.

Hope this helps

---

