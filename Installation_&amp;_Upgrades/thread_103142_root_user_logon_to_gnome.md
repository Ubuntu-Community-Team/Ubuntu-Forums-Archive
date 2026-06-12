---
title: "root user logon to gnome"
date: 2005-12-13
forum: Installation &amp; Upgrades
---

### Post by HosBosCos on 2005-12-13
i want to logon to gnome using root user cos' i can't reach files in my windows partition with other users. is there anyone who knows how to reach that files with other user or how to logon to gnome with root user? i already tried what it says in ubuntuguide but when i click login screen setup it says starting login screen setup but does not open anything. thx in advance:p

---

### Post by taurus on 2005-12-13
You can use the sudo command to gain access as root!  No need to log in as root directly because if you don't know what you are doing, you will trash Ubuntu and possible your Windows as well...

---

### Post by earobinson on 2005-12-13
I searced the forums for (root logon) and I found this [http://www.ubuntuforums.org/showthread.php?t=86811&highlight=root+logon](http://www.ubuntuforums.org/showthread.php?t=86811&highlight=root+logon) and many others.


VVVV Way better responce below VVVVVVVVVVV

---

### Post by aysiu on 2005-12-13
Are your Windows NTFS? [http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

Or perhaps FAT32?
[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

If you're not sure, type this command in a terminal: ```
sudo fdisk -l
```

If you don't know what a terminal is, go to Applications > Accessories > Terminal

You can also, if you need to browse as root, press Alt-F2 and type ```
gksudo nautilus
```

---

### Post by HosBosCos on 2005-12-13
thanx a lot.
and by the way my windows is ntfs. i can reach it with my root user but not others.
one more question does anyone know why my login screen setup does not open

---

### Post by earobinson on 2005-12-13
[QUOTE=HosBosCos]thanx a lot.
and by the way my windows is ntfs. i can reach it with my root user but not others.
one more question does anyone know why my login screen setup does not open[/QUOTE]
Im not sure what you mean?

---

### Post by aysiu on 2005-12-13
[QUOTE=HosBosCos]
by the way my windows is ntfs. i can reach it with my root user but not others.[/QUOTE] Follow these instructions: [http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

The instructions assume your Windows partition is at /dev/hda1
To be sure where it is, type ```
sudo fdisk -l
``` in the terminal.

---

### Post by HosBosCos on 2005-12-13
[QUOTE=earobinson]Im not sure what you mean?[/QUOTE]

i want to say that when i click system->administration->login screen setup it says starting login screen setup but nothing opens. thx

---

### Post by earobinson on 2005-12-13
are you logged in as root or as a normal user? Setting a root password can break some things

---

### Post by HosBosCos on 2005-12-13
i'm logged in as root

---

### Post by earobinson on 2005-12-13
that could be what is causing the problem, try it from the normal user.

---

### Post by HosBosCos on 2005-12-13
[QUOTE=earobinson]that could be what is causing the problem, try it from the normal user.[/QUOTE]


thx i'll try it.

---

### Post by HosBosCos on 2005-12-13
i tried it logging with an other user not root . it asks me password i enter and it disappears and nothing opens again.

and also i did the things it says in ubuntuguide to mount ntfs drives but i can't stiil access my windows partition with other users it says you don't have privileges. i enter sudo from terminal and look again but it shows my windows partition empty and in properties of drive it says unreadable.

it's hard to be a newbie :d thx a lot.

---

### Post by earobinson on 2005-12-13
dont use the root password, use the user password

> it's hard to be a newbie :d thx a lot. Just pass on what you learn and ill be happy :)

---

### Post by tay on 2005-12-13
i'm not sure if this what you were looking for..  
i really don't remember who showed me this,
but you can boot to grub, click e for edit the default
and then you have to e one of those options.. with -s at the end, or an s for single user.  i think it is on the image, maybe somebody else knows what i am talking about.

---

