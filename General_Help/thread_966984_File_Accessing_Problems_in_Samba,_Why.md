---
title: "File Accessing Problems in Samba, Why??"
date: 2008-11-01
forum: General Help
---

### Post by BigKapono on 2008-11-01
First, I'm a brand-new beginner.  I've found extraordinarily on-point help here, but have had no luck on this one.

I've got Samba up and running and can save .doc files from either machine onto my shared folder and access them with no problems in either place.

However, pdf's are another story.  

I've scanned a page into my Ubuntu machine and saved it to the shared folder-it can't be opened on the Windows machine.

I've saved a pdf from the web onto the Ubuntu machine, shared folder-it can't be opened on the windows machine.

But, if I save a pdf from the windows machine onto the shared folder, it can be opened on the Windows machine or Ubuntu.

I've got Adobe 9 on the Windows machine. 

I'm so confused...

Any ideas are much appreciated.  Please let me know what other info you might need to diagnose.

---

### Post by FrostyFlames on 2008-11-01
It could be that the permissions on the file don't allow the windows machine to read it. You can find the permissions by right clicking and selecting Properties -> Permissions (Gnome GUI).

This will have check marks or drop down menus for access. I'd compare the permissions from a PDF you can access to the one you can't and change the access permissions accordingly.

---

