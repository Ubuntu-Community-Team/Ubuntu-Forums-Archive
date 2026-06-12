---
title: "build-essential"
date: 2008-11-16
forum: General Help
---

### Post by steve228 on 2008-11-16
How can I download build-essential and all the packages it depends on without using 'sudo apt-get'?  

I cannot access the internet through ubuntu, but I can download files through vista and retrieve them in ubuntu.  I need build-essential so I can install madwifi and use my atheros wireless card.  It currently is not working, even with the newest Intrepid distro.

---

### Post by CatKiller on 2008-11-16
*build-essential* is on the cd, but not installed by default.

---

### Post by TeXtonyx on 2008-11-16
I think your installation cd may automount. Try

"A cd can be a repo like any other. The difference is that you are prompted for the cd when it is needed.

If you do not have the cdrom as the very fist repo on your list (it was there by default, you may have deleted it) you can make another entry for it from the command line.

sudo apt-cdrom add

sudo apt-get update

sudo apt-get install build-essential "

That may work. I think gcc is on the cdrom if not, which I believe
includes the make and configure stuff. This should let you build
build-essential after downloading the build-essential.tar.gz source.

---

### Post by Marius Derekus on 2008-11-16
Or you can go to [http://packages.ubuntu.com](http://packages.ubuntu.com) and search whatever package you need, their gauranteed to have it. (make sure you get all the required dependencies).

---

