---
title: "Problem installing apache."
date: 2005-12-05
forum: General Help
---

### Post by Rahu on 2005-12-05
I'm having a problem installing apache.
I run sudo apt-get install apache2

It get the message about whatever else it has to download and choose yes.
It then asks me to insert the disk "Ubuntu 5.10 _Breezy Badger_ - Preview i386 (20050908)" into the cdrom drive. The problem is that I do not have this cd.

I installed off of what I thought was the normal breezy cd, but I noticed immediately that it didnt have the graphics/login screen/whatever of breezy, so i did the dist-upgrade thing, and everything has been working fine, anyone know what's going on?

---

### Post by kosmic on 2005-12-05
No problem just go to synaptic 'repositories' and disable CDROM or as sudo edit the file /etc/apt/sources.lst and remove the line that have the CDROM.
 
Then do
 
sudo apt-get update
and voila :)

---

### Post by Rahu on 2005-12-05
thx ^_^

---

