---
title: "How to start the system"
date: 2009-07-10
forum: Installation &amp; Upgrades
---

### Post by janhalik on 2009-07-10
after running Kubuntu successfully without problem for 9months, suddenly it got switched to Ubuntu. now even system don't start. after running the Kubuntu screen it starts:

> Boot from (hd1,1) reiserfs xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx(all those numbers)
Starting up...
Loading, please wait...
Ubuntu 9.04 myname-laptop tty1


i have no idea what to do. when i wrote down startx, seemingly it booted into Ubuntu, but it was frozen. i'm sure it should boot from (hd0,0).

---

### Post by masux594 on 2009-07-10
hmm.. so, if i understand right, u have Kubuntu+ubuntu on your system.. right?

Sysc, A

---

### Post by janhalik on 2009-07-10
i had Kubuntu. it suddenly changed to Ubuntu. i tried to reinstall KDE but apparently couldn't get it work as a first choice. then it all crashed. 
reinstalling Kubuntu from CD would erase all my documents, wouldn't it?

---

### Post by masux594 on 2009-07-10
Well, it depends if when u installed the OS, u give a different partition fot /home directory.. Do you?

Sysc, A

---

### Post by janhalik on 2009-07-10
nope, the change to Ubuntu happened after i tried to install Avant Window Navigator... so i dare to think i don't have to separate systems

---

### Post by masux594 on 2009-07-10
So already u have a fresh install of Kubuntu.. If u want to keep docs, when you installed the OS you must create an additional partition /home where the OS work with this partition like if it were in the same partition.. otherwise, you can copy the docs that u need into an external drive or usb stick, then re-install the os and after copy the docs.. I think there's no other way..

Sysc, A

---

### Post by janhalik on 2009-07-10
i would consider doing that, but the trick is i cannot get into the system!

---

### Post by masux594 on 2009-07-10
Well, you can always copy your documents from the recovery mode of the OS.. are u able to boot in "recovery mode"?

Sysc, A

---

### Post by geekity2 on 2009-07-10
> **janhalik said:**
> i would consider doing that, but the trick is i cannot get into the system!

I think you should be able to mount the entire computer hard drive when running in the live distro mode off a live cd. That way you could mount an external HDD or a USB stick, as well as the internal HDD and copy across.

---

### Post by janhalik on 2009-07-10
> Well, you can always copy your documents from the recovery mode of the OS.. are u able to boot in "recovery mode"?

Sysc, Ano. it will go through many lines and then finishes with 'Ubuntu 9.04 myname-laptop tty1'
that's where it stops

---

### Post by masux594 on 2009-07-10
Well, during boot, press Ctrl+Alt+F1, you will splash into a command line..just try.. Am I right? Here you can copy all the files-directory that u wantwith the "cp" function..

Sysc, A

---

