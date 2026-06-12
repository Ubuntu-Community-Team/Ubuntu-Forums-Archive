---
title: "Why Can't my Packages be Authenticated"
date: 2005-11-12
forum: General Help
---

### Post by BabaFree on 2005-11-12
Any packages, whether I try to get them through synaptic or the command line, none of them can be authenticated.  Any thoughts as to why?

---

### Post by PMO6022 on 2005-11-12
In a terminal type ```
sudo apt-get update
``` and then try to install something.  If that doesn't work, please post your sources list: /etc/apt/sources.list

---

### Post by BabaFree on 2005-11-12
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted multiverse universe   
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted   multiverse universe   

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-updates main restricted multiverse universe   
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy-updates main restricted  multiverse universe   

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy universe 
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy universe 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security main restricted multiverse universe  
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security main restricted   multiverse universe   

# deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security universe 
# deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) breezy-security universe 




Here it is.  Hope it helps.  Ran update and still had the problem.
Thanks

---

### Post by PMO6022 on 2005-11-13
I really don't know if this will help, but it's worth a shot.  stick a "us" in front of "archive" for all the applicible sources.  In other words, change> deb [http://archive.ubuntu.com/ubuntu/]("http://archive.ubuntu.com/ubuntu/") breezy main restricted multiverse universe to ```
deb http://us.archive.ubuntu.com/ubuntu/ breezy main restricted mulitverse universe
```You'll have to update again after changing your sources list.  Good luck.  Sometimes one mirror will have problems that others don't.

edit: thanks dragoonz

---

### Post by dragoonz on 2005-11-13
> deb [http://us.archive.ubuntu](http://us.archive.ubuntu)**.con**/ubuntu/ breezy main restricted mulitverse universe

.com

---

### Post by aysiu on 2005-11-13
[QUOTE=PMO6022]I really don't know if this will help, but it's worth a shot.  stick a "us" in front of "archive" for all the applicible sources.[/QUOTE] Please don't recommend this. I spend a lot of time helping people get the *us* **out** of there because it causes so many gpg errors when people update. If anything, get the two *us* sources out of there that are already in there.

See the first link in my sig.

---

### Post by PMO6022 on 2005-11-13
Ok, I stand corrected.  I always thought it was preferred to use a local mirror to reduce the load on the main archive.ubuntu.com servers.

---

