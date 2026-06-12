---
title: "[SOLVED] Running an application on the menu with root privileges"
date: 2008-09-26
forum: General Help
---

### Post by oneadvent on 2008-09-26
I need to run zenmap with root privileges in order to have access to all the features in the program, so how can I add that to my menu where it asks for the password, or even where it doesn't?

Thanks for the help!

---

### Post by Idefix82 on 2008-09-26
You can click on the panel then "Add to panel" and then "Custom Application Launcher". Then specify the command to be something like "sudo zenmap" or "gksudo zenmap" depending on whether it is a command line or a GUI application.

---

### Post by oneadvent on 2008-09-26
awesome thats what I was trying to remember, gksudo, thanks a bunch.

---

