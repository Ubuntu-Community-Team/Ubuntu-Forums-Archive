---
title: "Buggyfox"
date: 2008-09-18
forum: General Help
---

### Post by PooAvenger on 2008-09-18
So...the other day I got off of firefox from browsing teh interwebs and today I get on and the address bar doesn't change from going from one tab to the other (ie. the last thing i typed in there is the only thing that ever goes in there) my book marks are all gone the back, stop, and refresh buttons dont work and my homepage has disappeared and won't load.

Can anyone help me fix this? I uninstalled firefox and then reinstalled 2.0 and it seemed to work but my addons and bookmarks were still gone (in 3.0 the addons are there).

Any help is appreciated :).

---

### Post by anotherdisciple on 2008-09-18
Well, I would suggest uninstalling FF2 and reinstall FF3. It is faster and better overall. Now, about your problems.

When you run a program for the first time in Ubuntu it will create a profile folder in you home directory. Firefox makes it in the folder ".mozilla". If you have major problems, often times something had corrupted in this profile, so the easiest thing is to remove it and start over.

If you uninstall firefox and reinstall, but you don't get rid of the old profile folder, you will likely have the exact same issues. So, here is what I suggest you do...

Open a terminal (Applications > Accessories > Terminal) and type this:

```
mv ~/.mozilla ~/.mozillabackup
```

That makes a backup of your old profile and removes the old one. That should solve the problem.

---

### Post by PooAvenger on 2008-09-18
Hey thanks! That did it!

Only thing left now is that my bookmarks aren't in firefox but I guess that's alright, yay delicious! :D

---

### Post by anotherdisciple on 2008-09-18
Cool... can you mark this as solved please?

---

