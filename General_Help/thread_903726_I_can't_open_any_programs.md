---
title: "I can't open any programs"
date: 2008-08-28
forum: General Help
---

### Post by nouseforaname7 on 2008-08-28
When I double click on a .exe it does nothing as does right clicking and choosing 'open'

---

### Post by jonian_g on 2008-08-28
That is because .exe is a windows format and not a linux one. Linux is not windows. You have to learn more about the os you decided to use.

The program installers for ubuntu and other debian based distros come with a .deb file.
To install programs in ubuntu go to panel menu Applications>Add/Remove, find a program in the list, check it, click apply and it will download and install automaticaly.

If you don't find the program in the list, or an equivalent, go to the program website and see if they have a .deb installer for download. Many windows programs don't have a linux version but you can find a linux alternative. Look for alternatives here:

[http://www.osalt.com/](http://www.osalt.com/) and here [http://www.linuxalt.com/](http://www.linuxalt.com/)

If you still want to use some windows programs and games then you have to install wine.
More info on wine here:

[http://www.winehq.org/](http://www.winehq.org/)

Also some universal linux installers come with .bin .sh .run etc.

---

### Post by Cheesehead on 2008-08-28
Failing to execute is the correct response for .exe files under Linux without Wine installed.

.exe means 'Windows executable file'. This isn't Windows. It's Linux.
Some (not all) Windows .exe files can be run using the Wine application.

Perhaps we can assist you further or help you find an alternative....what application, exactly, are you trying to open in Linux? What do want to do?

---

### Post by Taxman415a on 2008-08-28
If you're running the latest version of Ubuntu, 8.04 Hardy Heron, and you install Wine (either sudo aptitude install wine or through synaptic) then it does now setup the associations to try to run .exe files through wine. Wine is just not perfect because they have to try to reverse engineer all of Windows including the bugs. It does work well for some programs though.

---

