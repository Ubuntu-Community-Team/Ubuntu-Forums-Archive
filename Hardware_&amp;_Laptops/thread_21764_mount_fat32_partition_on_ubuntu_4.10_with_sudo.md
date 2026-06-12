---
title: "mount fat32 partition on ubuntu 4.10 with sudo"
date: 2005-03-23
forum: Hardware &amp; Laptops
---

### Post by stefansava on 2005-03-23
Hi,

I tried to mount my fat32 partitions and I went to 

/etc/fstab

and I tried to edit the text , but I cant do it because I think I need root access.

I cant edit anything from 

" / " 

Please, any help!

---

### Post by sunscape on 2005-03-23
yes you do need root... 

Try searching [www.ubuntulinux.org](www.ubuntulinux.org) for auto mount and follow the instructions. I should remind you that this should have been your first stop. Search first, ask questions later.

---

### Post by stefansava on 2005-03-23
Thanks!

I did ask and I tried many things but nothing seems to work !!  8-[

Hope to find something there!

---

### Post by stefansava on 2005-03-23
I tried to edit the file they say I should with

~$ sudo gedit /etc/fstab

and I get :

(gedit:5944): Gtk-WARNING **: cannot open display:


That's all


How else can I open it?

---

### Post by Buffalo Soldier on 2005-03-23
erm... are you running in windows mode(GUI) or command line?

If by any chance you find yourself stuck in command line interface after installation.. then try substituting **gedit** with **nano**. It's a text editor for command line.

---

