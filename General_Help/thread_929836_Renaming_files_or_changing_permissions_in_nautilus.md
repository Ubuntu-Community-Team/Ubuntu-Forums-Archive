---
title: "Renaming files or changing permissions in nautilus"
date: 2008-09-25
forum: General Help
---

### Post by tommygunner on 2008-09-25
I went to copy files to a folder in nautilus and I got a permission denied error. I then tried to rename a folder but no GUI drop down for rename. 

Of course I could do this from the terminal but I don't want to use the terminal. Is there a way to rename folders and change permissions through a GUI file manager?

---

### Post by aloshbennett on 2008-09-25
Launch nautilus using "gksudo nautilus" from a command prompt. Now you are running nautilus as root. Be careful what you are deleting and renaming :)

---

### Post by vanadium on 2008-09-25
Think twice if you have a "permission denied" error. It normally means you are not supposed to copy things there. If you know very well what you are doing, though, you should be acting as root, and aloshbennett showed you how you can run a graphical application with root privileges.

---

### Post by tommygunner on 2008-09-25
Cool, I'll have to create a link for that command so that when I want to get some stuff done, I'll be able to easily.

---

### Post by tommygunner on 2008-09-25
Interesting. I created a Launcher link to that command and see the rename field and permission field now. It still seems to be root even when I close the folder window. Do you know if it will timeout after 15minutes or so or will I be in Nautilus as root until I kill the process?

---

### Post by aloshbennett on 2008-09-26
Everytime you use the 'gksudo nautilus' launcher, nautilus would run as root. Ubuntu remembers your sudo, gksudo password for 10-15 mins.

Use the normal nautilus for all other file browsing.

---

