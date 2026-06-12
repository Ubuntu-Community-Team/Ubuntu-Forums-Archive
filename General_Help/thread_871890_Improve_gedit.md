---
title: "Improve gedit"
date: 2008-07-27
forum: General Help
---

### Post by xlinuks on 2008-07-27
Hi,
I think gedit needs some patches, so please share your opinions:
1) When I open a text file with gedit, even if the file has just a few bytes/letters in it - gedit keeps for **several seconds** a message in the status bar saying "Loading file (filename)". The user normally sees that message and waits until gedit "finishes loading" the file (which is btw only a few letters in my case), it makes gedit look exceptionally slow.

2) Same happens on saving the file, there's a message in status bar which disappears only after **several seconds** saying "Saving file (filename)", the user sees that and waits.. It again makes it look like an extremely slow program.

3) Since gedit is the default text editor in Gnome it should try to start faster, perhaps it's because of plugins, if so it should load plugins only as required, I dunno, but it must load faster.

This is one of the reasons why winXP users (rightfully though) have the impression that Ubuntu is much more slow.

The first 2 "bright features" seem to be implemented by M$ developers to scare new Linux users off :)
Anyway, does anyone think these 3 "features" need to be fixed?

---

### Post by Vadi on 2008-07-27
Ignore the status bar, in reality it does something as soon as the document is opened / the top saving bar closes.

---

### Post by xlinuks on 2008-07-27
Yes, I know that, it is just plain confusing, that's why I think it must be "fixed", and if you add other "weird" things you get the perfect reason why the Linux desktop is perceived as unhandy, that's why I wanna know whether the other users feel the same, if so I'll ask the devs to fix it.

---

### Post by Vadi on 2008-07-27
True. I'd say report it to the gedit bug tracker :)

---

