---
title: "dpkg/aptitude/synaptic problem!"
date: 2009-03-18
forum: Installation &amp; Upgrades
---

### Post by ChuckM on 2009-03-18
Posted this on the easpeasy forum, but I think I have more chance here.

Other than apt-get update , can't do anything.

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
root@laptop:~# dpkg --configure -a
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted
```

Any help would be greatly appreciated!
Running a fresh install (+ "the important security updates") of Ubuntu's Easy Peasy 1.0 on my EEE PC 701 4g

---

### Post by ChuckM on 2009-03-18
Any help? :(

---

### Post by markbuntu on 2009-03-18
Open a terminal and type

sudo dpkg --configure -a

type in your password when it asks and that should fix you up so aptitude and synaptic work again.

---

### Post by ChuckM on 2009-03-18
Yes, that's what I posted in the code section of the first post of the thread.

root@laptop:~# dpkg --configure -a    [that's me as root entering the command]

and the result is :

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted

---

### Post by ChuckM on 2009-03-19
last bump (and my last chance before I reinstall!)

---

### Post by oldos2er on 2009-03-19
This is a known bug: [https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/262451](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/262451)

---

