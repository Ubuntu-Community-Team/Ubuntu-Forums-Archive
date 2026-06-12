---
title: "2nd Harddrive"
date: 2005-03-05
forum: Hardware &amp; Laptops
---

### Post by Rahu Gaia on 2005-03-05
I just installed ubuntu and I have two harddrives one 9gb system drive and one 40 gb storage drive and I can not figure out how to make the 40 gb drive show up.

does anyone know how to do this, thanks for the help.

---

### Post by bored2k on 2005-03-05
[QUOTE=Rahu Gaia]I just installed ubuntu and I have two harddrives one 9gb system drive and one 40 gb storage drive and I can not figure out how to make the 40 gb drive show up.

does anyone know how to do this, thanks for the help.[/QUOTE]

> $sudo fdisk -l  will show u ur partition tables
find the one u want to *mount* and mount like this [the mount dir. has to be made forehand :
> $sudo mount /dev/hda1 /urdesireddir/


[http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)

---

### Post by Rahu Gaia on 2005-03-05
When I try to use the  $sudo fdisk -l it says it cannot open /dev/hda and /dev/hdb and when I try to mount those it does not work.

When I installed the os I formated both drives as ext3 and I gave the 2nd hd a mount point of /data.

---

### Post by Rahu Gaia on 2005-03-12
I was able to get this working now but I have another small problem that I hope someone can help me with. I need to edit my fstab file to make it mount everytime I boot but I can not seem to edit the file it seems to be stuck in read only mode how do I edit this file?

---

### Post by krusbjorn on 2005-03-12
[QUOTE=Rahu Gaia]I was able to get this working now but I have another small problem that I hope someone can help me with. I need to edit my fstab file to make it mount everytime I boot but I can not seem to edit the file it seems to be stuck in read only mode how do I edit this file?[/QUOTE]

did you do it in sudo mode?

sudo gedit /etc/fstab

---------------
edit typo.

---

### Post by Rahu Gaia on 2005-03-12
That worked thanks, this is my first time using linux.

---

### Post by krusbjorn on 2005-03-12
[QUOTE=Rahu Gaia]That worked thanks, this is my first time using linux.[/QUOTE]

you need root permissions to write to files outside your home directory. "sudo" is a way to execute a command with root permissions :)

---

