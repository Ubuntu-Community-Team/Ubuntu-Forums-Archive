---
title: "Add/Remove Program Error"
date: 2009-10-10
forum: Installation &amp; Upgrades
---

### Post by thisisthenewguy on 2009-10-10
ok so i tried to install a ds emulator, got this error. after trying to install more programs i relized the error is with the add/remove program. this is the error:

E: Method http has died unexpectedly!
E: Method /usr/lib/apt/methods/http did not start correctly
E: Unable to lock the download directory

any help would be greatfull

---

### Post by Partyboi2 on 2009-10-10
Hi, open a terminal (Applications>Accessories>Terminal) and try installing the program with
```
sudo apt-get install package
```
*replace package with actual package
If you get the same error message try reinstalling apt
```
sudo apt-get --reinstall install apt
```

---

### Post by thisisthenewguy on 2009-10-10
> **Partyboi2 said:**
> Hi, open a terminal (Applications>Accessories>Terminal) and try installing the program with
```
sudo apt-get install package
```*replace package with actual package
If you get the same error message try reinstalling apt
```
sudo apt-get --reinstall install apt
```

tried both, both times got error

E: Method http has died unexpectedly!
E: Method /usr/lib/apt/methods/http did not start correctly
 
thats the one i got in terminal

---

### Post by Partyboi2 on 2009-10-11
Try manually reinstalling apt. Go here and download the correct version of [[COLOR=Blue]apt[/COLOR]]("http://packages.ubuntu.com/search?keywords=apt&searchon=names&suite=all&section=all") and once downloaded double click on it and reinstall.
If that does not work I am all out of ideas.

---

