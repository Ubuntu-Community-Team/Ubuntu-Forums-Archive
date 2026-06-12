---
title: "scanner works under root only"
date: 2010-04-11
forum: Hardware
---

### Post by kornell on 2010-04-11
hi my beloved,

i've installed a xeroxphaser 3100 multifunction printer. Drivers available are only for ubuntu 7.1. I have 9.1. the printer works correctly (more or less). The scanner works only under root. I found on an italian forum this solution

sudo adduser $user lp
sudo adduser $user lpadmin

than restart session

what i receive back is:

silver@silver:~$ sudo adduser $silver lp
adduser: L'utente «lp» esiste già. (user already exists)
silver@silver:~$ sudo adduser $silver lpadmin
adduser: Il gruppo «lpadmin» esiste già. (group already exists)
silver@silver:~$ 

anyone can help?

---

### Post by ellgor on 2010-04-12
Hi,

You could try in a terminal :

sudo xsane

thats assuming you use xsane, change it to whatever you use, it is a permission issue (I have the same bother with an Epson) and make sure you have xsane-dev(libxsane-dev?), until a proper fix comes along.

Regards, Ellgor.

---

