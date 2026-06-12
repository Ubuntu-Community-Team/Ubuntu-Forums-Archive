---
title: "KDE broken.. Please help..."
date: 2005-11-26
forum: General Help
---

### Post by floyd27 on 2005-11-26
Hi..
I had to reinstall windows and lost grub..
So I then reinstalled GRUB and its workign fine..
However now when i try to log onto kubuntu or ubuntu. I cant.

It says "make sure DCOPserver is running"
So I went into the console and typed dcopserver.. I get dcopserver is already running. But if your sure it isnt remove //.DCOPserver_ubuntu_NODISPLAY

I tried to remove kubuntu and reinstall it but it wont let me do either.. I did an update and upgrade but also nothing......
Can anyone please help me fix this? Than guys...

---

### Post by ltmon on 2005-11-26
Can you try deleting the contents of the following directories, and try again:

~/.kde/cache-<hostname>
~/.kde/socket-<hostname>
~/.kde/tmp-<hostname>

where hostname is the name of your computer and "~" is your home directory.

These directories are all temporary, but can still screw up your kde installation if they get corrupted.  If reinstalling KDE didn't work then the problem likely lies here (because they will not get removed when you remove the kde packages).

L.

---

