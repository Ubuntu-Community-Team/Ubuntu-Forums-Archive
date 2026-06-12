---
title: "Spore Autorun Problem"
date: 2008-09-20
forum: General Help
---

### Post by Thyssenkrupp on 2008-09-20
Hey, i have a legit copy of spore, and im runnning 8.04.

Anywhoos, my problem is this:

When i try to run the discs autorun i get the following message

"Error starting autorun program: Permission denied"

how do i allow spore to run properly???

thanks!!

Jak

---

### Post by Bakon Jarser on 2008-09-20
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=13652](http://appdb.winehq.org/objectManager.php?sClass=version&iId=13652)

---

### Post by Thyssenkrupp on 2008-09-20
Where do i download the fixed.exe??

and can that run on any versions of wine??


thanks

---

### Post by Thyssenkrupp on 2008-09-20
Oh, i can get the file thing, i just dont know how to compile.patch it with wine

anybody know??

thanks

---

### Post by SpaceCadetMarko on 2008-09-20
> **Thyssenkrupp said:**
> Hey, i have a legit copy of spore, and im runnning 8.04.

Anywhoos, my problem is this:

When i try to run the discs autorun i get the following message

"Error starting autorun program: Permission denied"

how do i allow spore to run properly???

thanks!!

Jak

Hi, I have the same permission error problem when I try to run the installed from the disk. Did you manage to solve it?

I read through the Wine HQ page but it doesn't talk about this problem. Seems more like a local permissions type problem.

Thanks,
Mark

---

### Post by Bakon Jarser on 2008-09-20
Doesn't sound like a local permissions problem to me, but if it was you could solve it by running autorun as sudo.

```
cd /media/cdrom
```

```
sudo wine autorun.exe
```

Edit:  Are you guys running the latest version of wine?  Looks like all the people that got it running are using 1.1.4  or 1.1.5.  The version in the ubuntu repositories is 1.0

Edit:  Looks like you don't need the patch with wine 1.1.5.  Here's how to install it.

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

