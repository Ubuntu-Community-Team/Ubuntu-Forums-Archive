---
title: "Code safe to run?"
date: 2008-09-27
forum: General Help
---

### Post by Atsuko on 2008-09-27
> Ubuntu has a trash can/recycle bin feature similar to windows. The difference with Ubuntu is that you can empty the trash from the command line.

First you need to open your terminal and type the following command

Won't post the code here so you have to go to the page and look at it.

[http://www.ubuntugeek.com/empty-ubuntu-gnome-trash-from-the-command-line.html](http://www.ubuntugeek.com/empty-ubuntu-gnome-trash-from-the-command-line.html)

is it safe to run that code and can i put it in a launcher if it is safe?

---

### Post by Xiong Chiamiov on 2008-09-27
Yep, you're good.  Ubuntugeek's pretty good, but it's always a good idea to ask when coming across strange commands, especially those including rm -rf.

---

### Post by glotz on 2008-09-27
**rm** is the command to remove stuff

**-rf** are switches to the command that specify you want stuff to be removed recursively and including folders

**~/.Trash/*** is the target for the command, that is, everything in your trash folder


You can do a **man rm** to find out all about it. I suggest you try it. Manual pages are wonderful.

---

### Post by Atsuko on 2008-09-27
Thanks.

---

### Post by Elfy on 2008-09-27
Not sure it will work though, trash has moved in hardy into .local/share/Trash

---

