---
title: "Sun Java No Longer in Repos?"
date: 2008-11-07
forum: General Help
---

### Post by sstecken on 2008-11-07
Is Sun Java no longer in the repos?

I did an Alt. CD install of Intrepid and the repos seem to be all out of wack.  Can't search in the package manager properly and Sun Java 6 is nowhere to be see if I go through manually.  All the repos are checked and updated.

Edit: Also, a good old

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts 

fails.

---

### Post by ju2wheels on 2008-11-07
1. Make sure to remove the CD from the source list in software sources.

2. What is the error you get when installing.

---

### Post by sstecken on 2008-11-07
1. CD's were not checked.

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate

I solved the issue by just using
sudo apt-get install sun-java6-jre sun-java6-fonts

Neither of the packages show up in the package manager though.

---

### Post by ju2wheels on 2008-11-07
I assume you are using 64bit Ubuntu, so thats normal if you are. There is no 64bit version of the Sun Java plugin for web browsers. You will have to use the Icedtea alternative in order to run java applets in your browser.

---

