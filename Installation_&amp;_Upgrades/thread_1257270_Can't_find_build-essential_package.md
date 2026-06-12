---
title: "Can't find build-essential package"
date: 2009-09-03
forum: Installation &amp; Upgrades
---

### Post by brianmahler on 2009-09-03
I just installed Jaunty server edition on to a IBM server.   I am trying to add VMware - Server application , but when I add the packages required for VMware it complains that the package "Build-essential" is not present.   

I am using linux for the first time so I am very much a newbie. 
Brian

---

### Post by coffeecat on 2009-09-03
Don't forget that Linux is case-sensitive (unlike a certain other OS), so the package is "build-essential", not "Build-essential". Since you're running the server version I assume you don't have a GUI, so the command to install that from the command line is:

```
sudo apt-get install build-essential
```You might want to do a...

```
sudo apt-get update
```... first, to get your package list up to date.

---

### Post by stefangr1 on 2009-09-03
And what you also have to install (before you run into the next error message) are your kernel headers:

```
sudo apt-get install linux-headers-`uname -r`
```

---

### Post by brianmahler on 2009-09-04
Thanks for you reply's.   but my problem is still there.  here is the screen output

mwtadmin@mwtccxacs:~$ sudo apt-get install build-essential
[sudo] password for mwtadmin:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package build-essential

---

### Post by brianmahler on 2009-09-04
Thanks for you help, your tip update my package revealed the problem.   I did not have a DNS server identified and thus could not resolve any url names.    

it is now  crunching on the updates.
 
Thanks.

---

