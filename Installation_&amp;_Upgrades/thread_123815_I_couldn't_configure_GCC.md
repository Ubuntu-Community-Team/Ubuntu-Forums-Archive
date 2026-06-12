---
title: "I couldn't configure GCC"
date: 2006-01-31
forum: Installation &amp; Upgrades
---

### Post by g_rald23 on 2006-01-31
Apparently I don't have any GCC nor CC.. So I downloaded GCC-4.0.2, tried to install and configure it, but it failed.
.....
.....
checking for gcc.......no
checking for cc.....no
configure: error: no acceptable cc found in $PATH

I guess my question is, why is trying to look for gcc while I'm trying to install it???
FYI, I do not have an internet connection from the system that I'm going to be installing the GCC.

lookin' fwd for a reply to y'all Linux Engineer!:neutral: 

/*'desperate newbie'*/

---

### Post by amohanty on 2006-01-31
> sudo apt-get install build-essentials

will have most of the stuff you will need to compile apps from source.

HTH
AM

---

### Post by Sutekh on 2006-01-31
Make sure you have your Ubuntu installation CD in

Make sure that the cdrom is a repository for apt-get
```
sudo apt-cdrom add
```

Then get your packages
```
sudo apt-get install build-essential
```

---

### Post by softgun on 2006-01-31
gcc 4.0 IS installed by a default ubuntu brezy installation.
You may sometimes need 3.4 so install that as well (use synaptic or apt-get)
You also need to install make, which is missing in the default install.
Then add the build-essential package
Do
CC=gcc-3.4
export CC

Now you are ready to compile anything coming as source files (almost).

---

