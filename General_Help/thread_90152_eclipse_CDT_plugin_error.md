---
title: "eclipse CDT plugin error"
date: 2005-11-14
forum: General Help
---

### Post by nikolai.m on 2005-11-14
i was trying to install CDT plugin for eclipse3.1 (which i installed from kubuntu  repositories) and i get this error:
[INDENT]Unable to complete action for feature "Eclipse C/C++ Development Tools" due to
errors.
  Unable to create file
"/usr/local/lib/eclipse/plugins/org.eclipse.cdt.core_3.0.1/cdtcore.jar".
[/usr/local/lib/eclipse/plugins/org.eclipse.cdt.core_3.0.1/cdtcore.jar (No such
file or directory)]
  Unable to create file
"/usr/local/lib/eclipse/plugins/org.eclipse.cdt.core_3.0.1/cdtcore.jar".
[/usr/local/lib/eclipse/plugins/org.eclipse.cdt.core_3.0.1/cdtcore.jar (No such
file or directory)] [/INDENT]

any ideas on how to proceed from here on?
thnx

---

### Post by cstudent on 2005-11-14
You probably don't have the permissions to write to the directories. You should be able to open eclipse through the terminal using:

sudo eclipse

And then try installing CDT through Eclipse's update menu.

You could also temporarily change the owner of the directory eclipse resides in to your user account and install CDT.


Bill

---

### Post by nikolai.m on 2005-11-14
it works...
thnx Bill

---

### Post by cstudent on 2005-11-14
My pleasure. My good deed for the day is done. :)

---

