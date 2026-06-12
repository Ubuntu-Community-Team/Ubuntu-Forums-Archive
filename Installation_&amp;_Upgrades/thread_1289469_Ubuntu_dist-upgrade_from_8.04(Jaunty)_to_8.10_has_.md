---
title: "Ubuntu dist-upgrade from 8.04(Jaunty) to 8.10 has frozen at new Login screen!!"
date: 2009-10-12
forum: Installation &amp; Upgrades
---

### Post by scrypt on 2009-10-12
Hey Everyone

I have A Dell Studio 1737 Laptop.

I have been having a bit of trouble with Ubuntu.

I tried the dist-upgrade command from Ubuntu 9.04(Jaunty) to Ubuntu 9.10.  
 My system gave me the upgrade complete message.

I then rebooted. and now Ubuntu sticks and freezes at the new login screen.

Plus I cannot use my mouse pad it too is frozen.

Is there a way this can be fixed.

---

### Post by scrypt on 2009-10-12
I have tried these commands from the recovery console and it updated/upgraded quite allot of packages

But it did NOT fix my issue.

I still need some help please!

here are the commands I tried :

sudo dpkg --configure -a

sudo apt-get -f install

---

### Post by scrypt on 2009-10-12
Appologies in my post title I should have wrote that I was upgrading from Ubuntu 9.04(Jaunty) to Ubuntu 9.10.

NOT 8.04 to 8.10

---

### Post by scrypt on 2009-10-12
Ubuntu dist-upgrade from 9.04(Jaunty) to 9.10 has frozen at new Login screen!!

anyone offer any help??

---

### Post by scrypt on 2009-10-12
okay this is weird.

I can start and boot into ubuntu by using startx from the recovery console.
but I cannot use my mousepad, just my usb mouse.

But Ubuntu still freezes when I try to boot into the normal way (not recovery console)

can anyone help??

---

### Post by scrypt on 2009-10-12
okay i have fixed this issue using the same commands as earlier

I booted into the recovery console and ran

sudo apt-get install xorg-driver-fglrx

sudo aticonfig --initial

startx

login to ubuntu and then ran

sudo apt-get update

suao apt-get upgrade

---

