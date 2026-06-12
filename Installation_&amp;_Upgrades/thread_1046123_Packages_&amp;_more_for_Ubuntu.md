---
title: "Packages &amp; more for Ubuntu"
date: 2009-01-21
forum: Installation &amp; Upgrades
---

### Post by nagar.gaurav on 2009-01-21
Hi all,
I am using Ubuntu 8.10 and wanted to download packages for counterstrike and a free download manager or any other download manager Without Wine.
please help and post me the link or any command.
I am also facing a problem while downloading any package using the terminal this an error which is displayed in the terminal :-
for an example
------------------------------------------------------------------------------------------------------------
gaurav@gaurav -desktop:~$ sudo apt -get install spell
Reading package lists...... Done
Building dependency tree
Reading state information.... Done
Package spell is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package spell has no installation candidate.
-----------------------------------------------------------------------------------------------------------

This error shows up every time downloading any package from terminal and i am also unable to download from package manager.

please do help

---

### Post by Archmage on 2009-01-21
Please try the following command:

apt-get update

---

### Post by simtaalo on 2009-01-21
try getting the deb file from [www.getdeb.net](www.getdeb.net) and see if that makes any difference?

---

### Post by nagar.gaurav on 2009-01-21
> **Archmage said:**
> Please try the following command:

apt-get update

this dsnt wrk too

---

### Post by Tomatz on 2009-01-21
Are the repos enabled? Check in ***system, admin, software sources.***. Also, check out kget or gwget. They are great download managers and are in the repos. As for CS/CSS you will have to run them in wine as they are only available for windows. There is a nice game called urban terror available for linux that is quite like the original CS.


[http://www.urbanterror.net/page.php?6](http://www.urbanterror.net/page.php?6)

(second link down ".zip for mac and linux")

---

### Post by Tomatz on 2009-01-21
Make sure all boxes are checked in ***system, admin, software sources*** then "reload" the package manager (or *sudo apt-get update*).

Should have explained better ;)

---

### Post by oldos2er on 2009-01-21
> **nagar.gaurav said:**
> this dsnt wrk too

 Can you please copy and paste the output from "sudo apt-get update" here?

---

