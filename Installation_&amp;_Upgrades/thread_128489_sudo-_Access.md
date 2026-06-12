---
title: "sudo- Access"
date: 2006-02-11
forum: Installation &amp; Upgrades
---

### Post by scottlynn07410 on 2006-02-11
I need sudo access to manually remove a program to update my kubuntu system, can anybody help me do this.   -Thanks

---

### Post by Robgould on 2006-02-11
I'm not sure exactly what you are asking.  If you installed Kubuntu on your computer you should have sudo access already.  When you type a command in a terminal just preface it with sudo.  You will prompted for your password.  sudo is set up by default in ubuntu.

---

### Post by scottlynn07410 on 2006-02-11
Thanks,  I was not aware of that.
Also, am I correct in assuming the "password' you are refering to is my sign-on 
pass-word, or will sudo prompt me for a different password?

---

### Post by bluevoodoo1 on 2006-02-11
yup, the sudo password is your user password.

---

### Post by scottlynn07410 on 2006-02-11
thanks

---

### Post by scottlynn07410 on 2006-02-11
When I try to install software I Get this pop-up :

pkg: parse error, in file `/var/lib/dpkg/status' near line 6482 package `gnome-app-install':
 missing version

And I tried this : 
scottlynn07410@ubuntu:~$ sudo dpkg --configure -a

But I got this:

dpkg: parse error, in file `/var/lib/dpkg/status' near line 6482 package `gnome-app-install':
 missing version
 
What should I do ?
                          -Thanks

---

