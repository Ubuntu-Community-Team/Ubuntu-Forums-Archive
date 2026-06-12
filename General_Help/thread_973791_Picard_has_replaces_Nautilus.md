---
title: "Picard has replaces Nautilus"
date: 2008-11-07
forum: General Help
---

### Post by alexebird on 2008-11-07
Hello,

I just updated to 8.10 the other day and it's awesome, but I have been having an extremely annoying problem.  Whenever I try to open a directory from a shortcut, for example the Places>Home Folder shortcut in the main menu, it tries to open Picard instead of nautilus.

I had Picard on my 8.04 install, but I removed it after the update to 8.10 when I noticed the problem.  Unfortunately removing it didn't help.  I have removed all the files I can find related to picard, but that doesn't help either.

Here is the error dialog I get:

Could not open location 'file:///home/bird'

Failed to execute child process "picard" (No such file or directory)

Does anyone know whats up with this??

Thanks!

---

### Post by cariboo on 2008-11-07
This is a real common problem, mind you this is the first time picard was involved, Go to Places-->Hpme Foled and right click on any folder and select Open With Other Application and select **FIle Browser** from the Open With menu.

Jim

---

### Post by alexebird on 2008-11-07
Thanks a lot for the reply.  That wasn't quite what I had to do, but I got it fixed.  In an open instance of nautilus, I right clicked on a folder and went to "properties>open with" to set it to "File Browser" permanently.

---

