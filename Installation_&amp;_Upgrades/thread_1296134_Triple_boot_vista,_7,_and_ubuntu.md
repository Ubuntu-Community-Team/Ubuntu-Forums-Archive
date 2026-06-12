---
title: "Triple boot vista, 7, and ubuntu"
date: 2009-10-20
forum: Installation &amp; Upgrades
---

### Post by stevolime on 2009-10-20
I want to install windows 7 pro into my laptop that currently has vista premium and ubuntu so i can triple boot. Ubuntu is installed into vista. is there any way i can go about doing this without losing my data on my ubuntu setup?

---

### Post by Mark Phelps on 2009-10-20
As long as you create an empty partition and install 7 into that, essentially a new install, not an upgrade, all that will happen is that the MS Windows bootloader will be modified to include 7 as a selection -- in addition to the ones already there.

If you do an "upgrade" install, it's possible that, in attempting to preserve the existing Vista installation (by moving stuff into a windows.old folder), it might corrupt the existing Ubuntu install.

Also, have seen a lot of posts here about folks NOT being able to use Wubi with 7 successfully, so even if the upgrade goes OK, there's the possibility that the Wubi install will no longer work and you won't be able to boot Ubuntu anymore.

Don't know for sure, though; haven't tried this.  Always have Ubuntu installed to its own partition(s).

---

### Post by presence1960 on 2009-10-20
> **Mark Phelps said:**
> As long as you create an empty partition and install 7 into that, essentially a new install, not an upgrade, all that will happen is that the MS Windows bootloader will be modified to include 7 as a selection -- in addition to the ones already there.

If you do an "upgrade" install, it's possible that, in attempting to preserve the existing Vista installation (by moving stuff into a windows.old folder), it might corrupt the existing Ubuntu install.

Also, have seen a lot of posts here about folks NOT being able to use Wubi with 7 successfully, so even if the upgrade goes OK, there's the possibility that the Wubi install will no longer work and you won't be able to boot Ubuntu anymore.

Don't know for sure, though; haven't tried this.  **_Always have Ubuntu installed to its own partition(s)._**

+1

Wubi is not meant to be a permanent installation. It is to be used as a trial for those unwilling to commit to partitioning their hard disk **until** they see if they like Ubuntu. See here:

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

[http://en.wikipedia.org/wiki/Wubi_(installer)](http://en.wikipedia.org/wiki/Wubi_(installer))

---

### Post by stevolime on 2009-10-20
I really only run wubi cuz i dont hav the money to get a 2nd hard drive for my laptop. I just found it easier that way. Which it works fine. Im goin to try to do a triple boot cuz i do hav the extra space on the hard drive to make a decent size partition for windows 7, plus i just got windows 7 pro downloaded and i need to learn it.

Ill give it a try and write here if it works. I just have to wait for my hard drive to finish defraging.

Edit:

Ok, I got Windows 7 installed and Vista and Ubuntu work like normal.

---

### Post by Mark Phelps on 2009-10-21
Good to hear!  Did you do a "normal" install, or did you use Wubi?

---

