---
title: "[SOLVED] virtualbox OSE kernel problems"
date: 2008-09-07
forum: General Help
---

### Post by opossumjack on 2008-09-07
Hi...
I just installed the last version of VirtualBox OSE to use with VM inside ubuntu

But when I installed it it said that it has not the right kernel module to load...
Is there a way I can make it work???
Anyone has the same problem??

thanks in advance for your help

---

### Post by forger on 2008-09-07
Seems you're right.. there's no virtualbox-ose-modules-2.6.24-21-generic

Have you tried installing the older one:
```
sudo apt-get install virtualbox-ose-modules-generic
```

You can always use the non-OSE version at [www.virtualbox.org](www.virtualbox.org) > Downloads > Binaries

---

### Post by opossumjack on 2008-09-07
well... I tried it a few moments ago... It doesn't work...
I also tried reinstalling virtualbox ose... but when apt-get installs it it says "No suitable module for running kernel found."

---

### Post by opossumjack on 2008-09-07
I'm gonna try the non-OSE version...
Hope it will work... :)

---

### Post by forger on 2008-09-07
Well it works here :) It uses the kernel headers to compile the modules

---

### Post by opossumjack on 2008-09-07
It works!!!the non-OSE version works...

Tanks a lot...
You're very kind..

---

### Post by opossumjack on 2008-09-07
ok... 
I can't manage to start it...
which command I should use???
I can't find it in the menu... 
And If I try to start it in the terminal (I used "virtualbox") it says that virtualbox is not installed and that I should install the OSE version...

What can I do?

---

### Post by forger on 2008-09-07
[https://wiki.ubuntu.com/VirtualBox](https://wiki.ubuntu.com/VirtualBox)

You add yourself in the vboxusers group
```
sudo adduser $USER vboxusers
```

Then log out and log in again. VirtualBox is in Applications > System Tools > Sun xVM VirtualBox

---

### Post by opossumjack on 2008-09-11
ok... I've installed the non-OSE and then the OSE version, beacuse the non-OSE did not let me create the virtual disk... it just freezed... but now... the OSE version don't start by using the icon in the menu, and if I try to start it in terminal, it says that it is not installed...
I also installed the right module for my kernel...

what can I do?Now I'm trying to reinstall it... :(

---

### Post by eppo on 2008-09-11
the command is VirtualBox
take care to type the capital letters.

---

### Post by opossumjack on 2008-09-11
I've tried with virtualbox and VirtualBox... both did not work...
He says that virtualbox is not installed...

I'm gonna try to remove all the packages linked to VirtualBox and reinstall it from the beginning...

The strange is that when I installed it the first time, it worked with no problems...(apart from the kernel issue...)

---

### Post by opossumjack on 2008-09-15
It works!!!! :D

I've managed to make it work by deleting the config folder in my "home" directory...
I've made a clean install of the OSE version and now it works...

Thanks everybody for the support.
You're always very kind. :)

---

