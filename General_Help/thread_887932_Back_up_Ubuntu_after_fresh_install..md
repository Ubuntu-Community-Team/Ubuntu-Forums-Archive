---
title: "Back up Ubuntu after fresh install."
date: 2008-08-12
forum: General Help
---

### Post by johnny9794 on 2008-08-12
I have an old 20.05 gig hard drive laying here with me that i would like to use to backup my ubuntu partition image, My ubuntu partition is 16.07 gigs, "could someone point me in the correct direction" how would I go on about backing up ubuntu partition so that if I mess something up all i need to is restore it rather than reinstalling ubuntu and re downloading updates which is a waste of time if I may back up the os.

Thanx.

---

### Post by dje on 2008-08-12
try linbaku in my sig, it copies your entire installation into a tar archive that can be compressed. when restored your system is returned to the exact state it was in at the time of the backup

dje

---

### Post by johnny9794 on 2008-08-12
Great! Thank You.

---

### Post by colobix on 2008-08-12
Is it possible to create a backup image file withing installation program so it will be just like my ubuntu installation cd but with my programs and stuff?

---

### Post by dje on 2008-08-12
> **colobix said:**
> Is it possible to create a backup image file withing installation program so it will be just like my ubuntu installation cd but with my programs and stuff?

you probably want to use [remastersys]("http://www.remastersys.klikit-linux.com/")

dje

---

### Post by colobix on 2008-08-12
Yesss!!!!!! Thanks alot.

---

### Post by colobix on 2008-08-12
The dab package didnt work so I will have to do some research to find it another place. Remastersys
If u have an installation file for Remastersys that works, plz post a link here. Thanx.

---

### Post by dje on 2008-08-12
> **colobix said:**
> The dab package didnt work so I will have to do some research to find it another place. Remastersys
If u have an installation file for Remastersys that works, plz post a link here. Thanx.

the one attached to this post worked for me. after installing go to System >> Administration >> Remastersys Backup
are you using 32 bit or 64 bit ubuntu?

dje

---

### Post by louieb on 2008-08-12
When I'm about to do something that might trash my system like upgrading to the next release . I'll boot to the [SystemRescueCd]("http://www.sysresccd.org/Main_Page") and [use partimage]("http://ubuntuforums.org/showthread.php?t=287522") to backup my system.

---

### Post by pparks1 on 2008-08-12
> **colobix said:**
> The dab package didnt work so I will have to do some research to find it another place. Remastersys
If u have an installation file for Remastersys that works, plz post a link here. Thanx.

Change the deb line to read;
deb [http://www.remastersys.klikit-linux.com/repository](http://www.remastersys.klikit-linux.com/repository) remastersys/

---

### Post by colobix on 2008-08-12
Thanks alot. It works fine now. That remastersys is awesome!

---

