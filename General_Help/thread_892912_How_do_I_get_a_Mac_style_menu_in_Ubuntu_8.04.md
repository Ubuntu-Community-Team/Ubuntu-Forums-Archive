---
title: "How do I get a Mac style menu in Ubuntu 8.04?"
date: 2008-08-17
forum: General Help
---

### Post by michaelfougnie on 2008-08-17
I don't want menus (File Edit View ect) in programs. I want them on the top panel. I know its possible, but don't know how.

---

### Post by Genius314 on 2008-08-17
[http://code.google.com/p/gnome2-globalmenu/wiki/InstallingonUbuntu](http://code.google.com/p/gnome2-globalmenu/wiki/InstallingonUbuntu)

I'm not sure if it works with the latest kernels, gnome, etc, but that's the guide you want to follow. Keep in mind that it won't work with some programs (Firefox, and I think KDE programs), but it should with everything else.

EDIT: Well, it *seems* like it should work with Ubuntu 8.04, according to the guide (it says it's only for Gutsy, but then lists instructions for Hardy).

Also remember that you're working with system files and stuff, so if something goes wrong, you're going to have some troubles. (Although it seems that this just affects GTK, so the worst case scenario is that you have to boot to a terminal and reinstall GTK.)
Of course, I've done this before (with Gutsy, not Hardy), and it worked perfectly fine.

EDIT2: The guide doesn't go this far, so I'll just add this in case you (or anyone else reading) doesn't know. After following those instructions, just go to the top panel, right-click on an empty space, and click "Add to Panel." In the window that appears, select the global menu applet, and click the "Add" button. This should place it on your top panel. To delete it, and go back to the normal menus, simply right click on the menu, and click "Remove from panel."

Hope that helps (and makes sense)!

---

