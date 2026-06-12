---
title: "Failed install"
date: 2009-09-28
forum: Installation &amp; Upgrades
---

### Post by bgandy on 2009-09-28
I tried to install Ubuntu Server last night without success.  I downloaded a new copy, verified the MD5, burned a new disc, loaded the disc, checked it for errors, then attempted to load the software.  On the first attempt, It went all the way through install base system then failed at the end.  It popped up a red screen saying that a process did not install correctly.  
 
I then started over, I rechecked the disc, re-partitioned the drive.  It started to install the base system, then stopped and gave an error:
 
Debootstrap warning
Warning:  Couln't download package lidgdbm3
 
Press Continue,
 
Debootstrap warning
Warning:  [file:///cdrom/pool/main/l/linux-atm/libatm1_2.4.1-17.2_i386.deb](file:///cdrom/pool/main/l/linux-atm/libatm1_2.4.1-17.2_i386.deb) was corrupt
 
Press Continue,
 
Debootstrap warning
Warning:  Couldn,t download package libat1
 
Press continue,
 
Debootstrap warning
Warning:  Failure while configuring base packages.  This will bee attempted 5 times.
 
Press continue,
 
The computer continues to load then gives a message that no installable kernel was found in the defined APT sources.
 
 
This is the same thing that happenend last night.  I have burned a new disc at a lower speed (8x) and had the same problem.
 
Any suggestions?

---

### Post by prsinghdua on 2009-09-28
I had a similar problem when installing linux on my laptop with netboot. What I did was go to manual install and what it does is install the base system and then you can install whatever you want through apt. I installed xubuntu by typing
```
sudo apt-get install xubuntu-desktop
```
You should be able to find a package for ubuntu server too.
Hope that helps!:)

---

### Post by bgandy on 2009-09-28
Where can I get that package.  It is the base system that fails the install.

---

### Post by bgandy on 2009-09-28
So I tried installing Ubuntu Desktop edition on the same PC.  It to had a similar error.  Any help would be appreciated.  I have already repartitioned the computer so it is useless until I get thi fixed.
 
Thanks

---

### Post by Simonft on 2009-09-28
Try the minimal install cd. [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by bgandy on 2009-09-29
The minimul install worked.  Of course it is command line, and I really need the server edition to accomplish my goal easily.  Is there a way to upgrade, or add the packages I need?

---

