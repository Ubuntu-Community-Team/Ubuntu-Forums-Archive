---
title: "Graphics tablet doesn't work properly."
date: 2010-05-09
forum: Hardware
---

### Post by stripedxii on 2010-05-09
I have a DigiPro WP5540 Pen Tablet which worked with Ubuntu 9.10 with the wizardpen driver and all but it doesn't work properly when I installed Ubuntu 10.04.  Here's the deal:


[LIST]
[*]Hovering the stylus above the pad does move the cursor around
[*]If I press LIGHTLY, it does does do left clicks (drawing), but if I were to press harder the  cursor freezes and will only move if I have the stylus against the pad, which would cause it to draw everywhere.  This fixes if I unplug the tablet and plug it back in.
[*]The button on the stylus that does right mouse clicks works fine
[/LIST]

[LIST]
[*]Pressure sensitivity does not work
[/LIST]

I just don't know what to do.  I tried looking at these topics
[http://ubuntuforums.org/showthread.php?t=1469380](http://ubuntuforums.org/showthread.php?t=1469380)
[http://ubuntuforums.org/showthread.php?t=1475433](http://ubuntuforums.org/showthread.php?t=1475433)
[http://ubuntuforums.org/showthread.php?t=228991](http://ubuntuforums.org/showthread.php?t=228991)

and this thing [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)

Can someone please help?

---

### Post by irishbandit on 2010-05-10
Have you edited /usr/lib/X11/xorg.conf.d/70-wizardpen.conf
and added options for your tablet?
You might want to add the values for your tablet
   Option "TopX" ""
   Option "TopY" ""
   Option "TopZ" "10"
   Option "BottomX" ""
   Option "BottomY" ""
   Option "BottomZ" ""
edit the topz so you have to press harder for it to draw.
I am going to change mine to 20 or 30.

---

### Post by stripedxii on 2010-05-10
I have those options in that file.

EDIT: The tablet works perfectly if I switch "MatchIsTablet" to "MatchIsPointer" in 70-wizardpen.conf, but if I move my USB mouse the cursor instantly goes to the top left of the screen.  I don't know how to fix that...

---

### Post by andrew87 on 2010-05-28
I have the same problem, stirpedxii, have you found a solution in this time?

---

