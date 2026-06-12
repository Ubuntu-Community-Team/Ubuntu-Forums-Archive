---
title: "[SOLVED] How do I delete stubborn files?"
date: 2008-09-10
forum: General Help
---

### Post by Linux user 66 on 2008-09-10
I've got two folders in my Trash bin containing some files that just won't be deleted.

How can I remove them?

I'm running Ubuntu 8.04.1 64-bit.

---

### Post by Tom--d on 2008-09-10
They will not remove because you dont have the permission to. 

You need to login as root and delete them.
Do this command and locate the folder in your home and delete it.

```
gksu nautilus
```

---

### Post by Linux user 66 on 2008-09-10
> **Tom--d said:**
> They will not remove because you dont have the permission to. 

You need to login as root and delete them.
Do this command and locate the folder in your home and delete it.

```
gksu nautilus
```

I used the command, but when I selected *Trash* I was given an error message saying that *The folder contents could not be displayed*. However, when I select *Trash* from the desktop, I can always see the two folders containing the stubborn files. 

Is there anything else I could do?

---

### Post by tuxxy on 2008-09-10
If the files are in your users trash, open a terminal and paste this

```
rm -rf ~/.local/share/Trash/*
```

---

### Post by WRDN on 2008-09-10
This will forcibly remove all files and folders in the Trash folder.

```
sudo rm -rf ~/.local/share/Trash
```

---

### Post by -Zeus- on 2008-09-10
```
sudo rm -rf ~/.local/share/Trash/*
```

This will empty the trash of the user you're logged in as.

EDIT: CRAP!

---

### Post by kokkus on 2008-09-10
Here you go.

just type
sudo -s
this is it. u r root now. then u can create a root account.

sudo su -

'su -' switches you to to the super user (root) account. The dash means 'run the login scripts'. The sudo is required to give the current user priviledges to use the su - command.

---

### Post by Linux user 66 on 2008-09-10
> **WRDN said:**
> This will forcibly remove all files and folders in the Trash folder.

```
sudo rm -rf ~/.local/share/Trash
```

This command worked! Thanks a lot, you guys! :)

---

### Post by Iowan on 2008-09-10
From a gnome-type terminal (not CTRL-ALT-F1):```
cd ~/.Trash
ls -al
```If troublesome files are there, click/drag to highlight the name, then use pulldown Edit, select Copy. Then try **sudo rm** {use pulldown Edit, select Paste}.  IF there are any weird non-printable characters, this might catch them. Or, **sudo mv {paste} /dev/null**
It's a more complicated approach than just **sudo rm ***, but seems to work.  Sometimes, surrounding the offending name with quotes makes it delete-able.

---

