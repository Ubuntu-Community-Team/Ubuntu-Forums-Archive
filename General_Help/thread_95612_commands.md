---
title: "commands"
date: 2005-11-26
forum: General Help
---

### Post by teaker1s on 2005-11-26
first I used a command that showed a list of all device paths of harddisk and cdrom and I can't remember it- please can someone remind me
Secondly where would I find a complete set of commands that can be used in console as help on ubuntu is limited there isn't even xkill listed

thanks

---

### Post by jliedeka on 2005-11-26
df shows the filesystems, mount points size of partitions, amount used and free.  Is that what you were looking for?

Second, ls /bin /sbin /usr/sbin /usr/bin /usr/X11/bin but it may be more helpful to search the man pages with apropos (man -k)

---

### Post by taurus on 2005-11-27
Or for easy to read, use

df -h

---

### Post by dodongo on 2005-11-27
One of the things that I've come to love about lurking in the Ubuntu Forums to give help to people who're encountering the same problems I did when I got started... is learning new things like this!  Cheers!

---

### Post by teaker1s on 2005-11-27
I was looking more for the command that shows paths of all drives eg
cdrom1 /media/cdrom1
annoying as It is I cann't find the command I used before

thanks

---

### Post by Bachstelze on 2005-11-27
gedit /etc/fstab

I also recommend this site to learn the command line : 

[http://www.linuxcommand.org/index.php](http://www.linuxcommand.org/index.php)

---

### Post by taurus on 2005-11-27
Go get yourself a Linux in a Nutshell from O'Reilly...

---

### Post by teaker1s on 2005-11-27
remembered the command its 
sudo fdisk -l

---

### Post by Bachstelze on 2005-11-27
[QUOTE=teaker1s]I was looking more for the command that shows paths of all drives eg
cdrom1 /media/cdrom1[/QUOTE]

Since when does fdisk -l show you the cdrom ?

---

