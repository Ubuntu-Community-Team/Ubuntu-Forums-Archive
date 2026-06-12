---
title: "[SOLVED] Whats going on with the os!!!???"
date: 2008-09-23
forum: General Help
---

### Post by Hyper Tails on 2008-09-23
HELP!!! I Can'T USE KUBUNTU ANY MORE AND NOW IT SHOWS UP THIS STUPID TEMENMAL screen AND IT attempts TO sHOW THE mONITOR AND ALL IT DOES IS PERVENT me from logging in and using the os!!!!

Please THIS is  A SEIOURES issue!!

---

### Post by phidia on 2008-09-23
At the terminal try entering > xfix and/or > sudo dpkg-reconfigure xserver-xorg
If none of that works try to start the xserver > startx and notice and report the specific error messages.

---

### Post by Hyper Tails on 2008-09-23
okay it works but now it doesen't have a login screen or a log out screen
and it can't shut down untill i type

```
sudo poweroff
```

any other suggestions?

---

### Post by phidia on 2008-09-23
Maybe try > sudo apt-get update && sudo apt-get upgrade
What version of Ubuntu are you using?

---

### Post by Hyper Tails on 2008-09-23
never mind it's working now

---

