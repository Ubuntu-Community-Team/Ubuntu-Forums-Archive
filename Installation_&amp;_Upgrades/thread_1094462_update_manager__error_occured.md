---
title: "update manager  error occured"
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by rdema19403 on 2009-03-12
i just i unstalleed ubuntu 8.10 on my computer and iwent to intall the upates an i get error occured i not really sure what it means E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
 this is the first time iam  using this software. thanks in advance 
ralph

---

### Post by howefield on 2009-03-12
Open a terminal (Applications > Accessories > Terminal) and type the following.
```

sudo dpkg --configure -a
```

You will be asked for your password, type it, press enter and hopefully you'll be sorted.

---

### Post by taurus on 2009-03-12
Close down the update manager first.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by avtolle on 2009-03-12
Open a terminal (from the top panel, click on Applications, then from the list, click Accessories, then select Terminal) and then at the prompt in the terminal do```
sudo dpkg --configure -a
``` which will then request your password. Type in the password you use to log in (**you will not see any visual confirmation not even ***) press Enter. If you get any error messages, paste them here.

---

