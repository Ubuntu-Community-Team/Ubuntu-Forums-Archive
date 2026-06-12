---
title: "How do you make normal desktop icons just like in Windows?"
date: 2008-08-27
forum: General Help
---

### Post by Timberwolf5578 on 2008-08-27
I would like to be able to make desktop shortcuts and folders just like in Windows.  How is this done in Ubuntu?

Thanks.

---

### Post by xravexheavenx on 2008-08-27
what do you consider as a "normal desktop icon"?

---

### Post by Timberwolf5578 on 2008-08-27
I mean how do you put a trash can, documents, my computer etc shortcuts on the desktop?

---

### Post by mb_webguy on 2008-08-27
If you're using Ubuntu, right-click on the desktop and select "Create Launcher".  Type in the name you want to be displayed under the icon, then either type in the command to launch the program (if you know it), or else click browse to locate the program.  Applications in Linux are almost always installed to either the /usr/bin or /usr/local/bin folders.  Also, if the program is listed in your Applications menu, you can right-click on the menu, select "Edit Menus", locate the program, right-click and select "Properties" to view the information you need for the desktop launcher.

When you enter the command for the applications, the icon should usually be automatically set for you.  If not, you can click on the icon button to browse for it.

When you're done, click "OK", and you're done.  It may seem like a lot of work, but that's only because I gave you the detailed instructions.  I could have said "right-click on the desktop, select Create Launcher, and fill in the information".

EDIT:  Also, you could just right-click on an item in the Applications/Places/System menu and select "Add this launcher to desktop".

> **Timberwolf5578 said:**
> I mean how do you put a trash can, documents, my computer etc shortcuts on the desktop?
If that's all you want, ignore the above and type "gconf-editor" in the terminal.  (If you get a "command not found" message, type "sudo apt-get install gconf-editor" to install it, then try again.)  Navigate to apps->nautilus->desktop, and check the icons you want on the desktop.

---

### Post by mcduck on 2008-08-28
For the "default" desktop icons, Press Alt-F2 and run "gconf-editor". Then browse to apps/nautilus/desktop and enable whatever icons you want.

For program launchers, just right-click a program in the menu and you'll get the option to add a launcher to desktop. Or just drag&drop items from the menu to desktop.

---

