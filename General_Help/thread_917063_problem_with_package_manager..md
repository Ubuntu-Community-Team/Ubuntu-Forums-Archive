---
title: "problem with package manager."
date: 2008-09-11
forum: General Help
---

### Post by jkc2103 on 2008-09-11
hey,
Im sort of new with ubuntu.. but anyways i was trying to install something. and  i was following instructions on how to do it.. well it wanted to me to edit somthing in the source file.. and i added something to it at the bottom and then clicked save. but now it wont let me install anything..  heres what i get.   

E:Type 'kate' is not known on line 60 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

I tired to edit it again..  and it wouldn't let me. and it told me that i have to be a root user. which im the  admin on this ubuntu. so what should i do?

---

### Post by knattlhuber on 2008-09-11
There's a faulty line in /etc/apt/sources.list. That's usually easy to fix.

Can you please post the output of

```
tail /etc/apt/sources.list
```

Or, alternatively, you can try to fix it yourself using

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by jkc2103 on 2008-09-11
oh wow. lol thanks =] 
oh what programs are good to upload to extract and install  apps?

edit:
what are some good programs to open up .rar files etc.

---

### Post by anystupidname on 2008-09-11
Line 60 of your /etc/apt/sources.list has a reference to "kate" which doesn't belong there. In case it helps, here is an example of a good sources.list

```
# Ubuntu supported packages
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu hardy main restricted
deb http://us.archive.ubuntu.com/ubuntu hardy-updates main restricted
deb http://security.ubuntu.com/ubuntu hardy-security main restricted

deb-src http://us.archive.ubuntu.com/ubuntu hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hardy-updates main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu hardy universe multiverse
deb http://us.archive.ubuntu.com/ubuntu hardy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu hardy-security universe multiverse

deb-src http://us.archive.ubuntu.com/ubuntu hardy universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu hardy-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security universe multiverse

# Ubuntu backports project
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu hardy-backports main restricted universe multiverse

deb-src http://us.archive.ubuntu.com/ubuntu hardy-backports main restricted universe multiverse

```

In the future, I highly suggest creating backup copies of any files before editing them. Example:
cp /path/file-imgonna-edit.ext  /path/filename.ext.20080912

---

### Post by jkc2103 on 2008-09-11
thanks. what are some good programs to  decompress?  example like  winzip and  what ftp programs are usefull in ubuntu?

---

### Post by knattlhuber on 2008-09-11
Archive Manager is pre-installed. If you right-click a compressed file, the menu will offer you "Open with Archive Manager" or "Extract here".
There are probably tons of others. You could go to Applications > Add/remove and search for 'zip' or 'archive' or 'compress' and find them.

---

### Post by jkc2103 on 2008-09-11
thanks =]

i just got  KDE session running.   whats a good ftp program that i can use?

---

### Post by knattlhuber on 2008-09-11
I use Filezilla, but, again, there are tons of others. A search as described above will list them. You'll find even more on google..

---

### Post by jkc2103 on 2008-09-11
cool. what are some customizations you can do on kde?

oh sry for so many questions. but how to do you open tar.gz  in kde?

---

### Post by knattlhuber on 2008-09-11
Ugh. No idea. I'm on Gnome.
You will probably find tons of threads on KDE customization on this forum. The search function is your freind :)

PS: Please don't forget to mark this thread as solved (under Thread Tools in the right top corner).

---

