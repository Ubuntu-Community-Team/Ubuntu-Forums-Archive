---
title: "Synaptic - Remove Packages... and their dependencies!"
date: 2005-11-18
forum: General Help
---

### Post by Yoda_Oz on 2005-11-18
Hi,
I've noticed that if i install, say amarok through synaptic, synaptic automatically installs all the kde dependencies and stuff...
...but if i remove amarok it only removes amarok and not the kde dependencies that it needed in the first place and it is obvious that the kde dependencies arent needed any more because there arent any other apps that need them on my ubuntu box.
do you think there is a to do list with synaptic and this is one of the things they are working on? so that if a package is removed synaptic looks at the dependencies and if no other program depends on them they are deleted too...
is there a way around this apart from having to look at the amarok package and look for its dependencies and then delete them one by one?

---

### Post by Efwis on 2005-11-18
[QUOTE=Yoda_Oz]Hi,
I've noticed that if i install, say amarok through synaptic, synaptic automatically installs all the kde dependencies and stuff...
...but if i remove amarok it only removes amarok and not the kde dependencies that it needed in the first place and it is obvious that the kde dependencies arent needed any more because there arent any other apps that need them on my ubuntu box.
do you think there is a to do list with synaptic and this is one of the things they are working on? so that if a package is removed synaptic looks at the dependencies and if no other program depends on them they are deleted too...
is there a way around this apart from having to look at the amarok package and look for its dependencies and then delete them one by one?[/QUOTE]
I don't know if there is a todo list that this issue is being addressed in. you could always check bugzilla on that.

As for a way to get rid of those no longer used files you can do the folllowing:

```
sudo apt-get install deborphan
```
after it installs run it via terminal
```
$ deborphan
```
This will list all those orphaned dependancy files on your hdd. so you can delete them. 
then just use **sudo apt-get remove <filename>** in terminal to remove them one at a time. You may have to run it a couple of times to get them all removed, but it works.

---

### Post by mcduck on 2005-11-18
after instaliinkg deborphan you can also use it with synaptic. Open Synaptic, go to Settings/Filters and create a new filter called Orphaned, make it show only orphaned packages and save. Now you only have to click the 'Custom' button in bottom left of Synaptic window, select Orphaned and it will list all your unneeded packages..

---

### Post by Efwis on 2005-11-18
[QUOTE=mcduck]after instaliinkg deborphan you can also use it with synaptic. Open Synaptic, go to Settings/Filters and create a new filter called Orphaned, make it show only orphaned packages and save. Now you only have to click the 'Custom' button in bottom left of Synaptic window, select Orphaned and it will list all your unneeded packages..[/QUOTE]
heh, you learn something new everyday around here. I didn't know about that. :)

---

### Post by Yoda_Oz on 2005-11-18
fan...bloody...tastic!

---

