---
title: "[SOLVED] Ubuntu start up logo is kubuntu's after installing kde 4 and then removing i"
date: 2008-10-03
forum: General Help
---

### Post by Hyper Tails on 2008-10-03
hi i run hardy heron and i installed kde 4 inside ubuntu (not kubuntu) i used the add/remove package manager to install it and then ubuntu had it's first crash then i restarted it and i said give the ubuntu logo (just for fun) and then i say the kubuntu one instead.
then confusion rained and i was like what the beep happened to ubuntu 
and then it showed up the login screen which was the ubuntu one and i had alright now there something wrong here

and i opened firefox and it's home page was this (it's solved)

file:///usr/share/ubuntu-artwork/home/index.html

please help 

help will be highly thanked 

thank you

---

### Post by Hyper Tails on 2008-10-03
...................................................................
..................................................................
..............................................................
....................................................
..............................................................

---

### Post by Hyper Tails on 2008-10-04
:confused: Please :confused:

---

### Post by terry_gardener on 2008-10-04
you could try the following command taken from website.[http://ubuntu.wordpress.com/2006/02/20/restoring-the-ubuntu-usplash-after-a-kubuntu-install/](http://ubuntu.wordpress.com/2006/02/20/restoring-the-ubuntu-usplash-after-a-kubuntu-install/)

sudo update-alternatives --config usplash-artwork.so

hope this helps.

---

### Post by Stefanie on 2008-10-04
open up a terminal and enter this command:

```
sudo update-alternatives --config usplash-artwork.so
```

you will be asked which splash screen you want to use. pick the ubuntu one. 
after doing this you need to issue this command
```
sudo update-initramfs -u
```
to update the splash screen settings.

---

### Post by bconover on 2008-10-04
That command didn't work for me back when I installed KDE. I reinstalled the ubuntu splash via Synaptic (look for usplash-theme-ubuntu)

---

### Post by Hyper Tails on 2008-10-04
I got it thank you su so so so so so much !!!!1111!!!!

---

