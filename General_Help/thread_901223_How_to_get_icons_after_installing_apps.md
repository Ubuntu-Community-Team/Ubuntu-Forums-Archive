---
title: "How to get icons after installing apps?"
date: 2008-08-26
forum: General Help
---

### Post by JayUK20 on 2008-08-26
I have installed some apps and the only way to run them is by using the run command but I want them to display in my app menu and on my desktop, how to I do this?

---

### Post by kpkeerthi on 2008-08-26
Right-click on Applications, choose Edit Menu. You should able to add new menu items there.

---

### Post by JayUK20 on 2008-08-26
Thanks, I have already tried that but the icon isn't there!

---

### Post by Too Late on 2008-08-26
Press the "New Item" button in the upper right corner. If you want to change your icon (or was that your only problem?), press the icon picture in the window which just opened. Or if you want change it later, right-click the menu entry and select properties.

If the problem is that you don't have a specific icon there, that's a different case. Maybe you can make one with gimp.

---

### Post by JayUK20 on 2008-08-26
I don't want to change an icon, I want to add an application to the app menu and the desktop.

---

### Post by Too Late on 2008-08-26
So after you have created the launcher, does it immediately disappear, or can you still see it in the Main Menu editor? Try logging out and in, if that makes it visible in the actual menu, too.

You can make a desktop icon by right-clicking on the desktop and select Create Launcher. The opening pop-up window is similar to that you've just seen in the Main Menu editor.

---

### Post by bankg3 on 2008-08-26
how did you install these apps? if you used aptitude or apt-get you should already have the items available either in the menu editor or just by default, but that isn't your case so it sounds like you installed them from source files.  If that is the case you have to manually create them as described above by Too Late.  You do need to know where you installed these apps to though, because all of their icons will most likely be stored in the folder created during installation

---

### Post by JayUK20 on 2008-08-26
This was just a .deb package.

---

### Post by bankg3 on 2008-08-26
you can type
```
dpkg -L (package name)
```
and find it's installed location to find the icons

---

