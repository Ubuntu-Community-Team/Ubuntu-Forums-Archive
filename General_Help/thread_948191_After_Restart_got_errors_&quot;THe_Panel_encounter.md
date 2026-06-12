---
title: "After Restart got errors &quot;THe Panel encountered a problem while loading OAFIID:...&quot;"
date: 2008-10-15
forum: General Help
---

### Post by dunskii on 2008-10-15
Hi all,
I think I have made a boo boo, basically I was trying to install a group of codecs, they didnt work so i did an apt-get remove.  Anyways I didnt read the waring properly (due to being a windows user for years) and a hole lot more than just the codecs were removed. so i did an update hopeing everything would go back to normal.
After the restart I got 3 error boxes when I logged in 
THe Panel encountered a problem while loading OAFIID:GNOME_StickyNotesApplet
THe Panel encountered a problem while loading OAFIID:GNOME_PANEL_TrashApplet
THe Panel encountered a problem while loading OAFIID:GNOME_GWeatherApplet

All of them then have the question
Do you want to delete the applet from your configuration.
Which I tried delete with out any success.

My first question is how to fix the errors,
The second, is there anyway to recover the stickynote data

If I have learnt anything from this it is to Listen to Linux when it asks a question.

Thanks in advance.
D

---

### Post by _sebastian_ on 2008-10-15
not sure if this helps but when you start up synaptic you can have a look at the history of things you installed and removed.

on there you should find all the packages you removed accidentally.
I guess if you select the right one again for installation the dependencies should pull all other needed packages back in.

---

### Post by dunskii on 2008-10-15
Thanks Sebastian,
When I looked at the synaptics i saw gnome applets was uninstalled  after reinstall everything a ok.
Lesson leart i guess.
D

---

### Post by _sebastian_ on 2008-10-15
glad I could help

---

