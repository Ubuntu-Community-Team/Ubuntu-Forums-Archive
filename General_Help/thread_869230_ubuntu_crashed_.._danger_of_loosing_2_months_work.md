---
title: "ubuntu crashed .. danger of loosing 2 months work"
date: 2008-07-24
forum: General Help
---

### Post by ima998 on 2008-07-24
hi,

I have ubuntu 7.10

Earliar I got an error called "Error 22" at startup and couldnt go to booting page,
then after reading about it i found out that its something to do with the GRUB bootloader ,Then I reinstalled GRUB boot loader from ubuntu CD(from  repair option)

Now I can go  to the booting options (this mechine is dual boot system),
But when I choose ubuntu it askes me to enter an username and a password,(looks like its trying to boot on console mode)

my previous username and password doesnt work on this. 

please can anybody help me? two months of project work is in danger :(

thanks in advance

---

### Post by jordilin on 2008-07-24
don't know exactly what is going on here, but you can always boot from live cd, mount the hard drive, backup the data (your 2 months work) to an external hard drive, restart and install again. Apparently that could be a problem with the master boot record (mbr).

---

### Post by WRDN on 2008-07-24
Boot into recovery mode, and select to drop down to root prompt (second option). Now, type:

```
passwd [username]
```

This will allow you to change your password.

Alternatively, you could create a new user to login with:

```
adduser [username]
```

---

### Post by ima998 on 2008-07-24
thanks guys ,

Do I have to get Ubuntu live CD seperately or is it the same one I installed ?
confused

---

### Post by jordilin on 2008-07-24
Ubuntu install cd is a live cd already. I'm highly sure you did not download the alternate one ;). Put the cd, restart and boot. You will see quickly if it is a live cd

---

