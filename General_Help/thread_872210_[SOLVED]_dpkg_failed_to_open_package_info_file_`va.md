---
title: "[SOLVED] dpkg: failed to open package info file `/var/lib/dpkg/available' for reading"
date: 2008-07-27
forum: General Help
---

### Post by morbid_bean on 2008-07-27
Simply trying to install wine via terminal....

do the sudo aptitude update (also tried sudo apt-get update)

```
jimbo@Monster:~$ sudo aptitude install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following NEW packages will be automatically installed:
  binfmt-support winbind 
The following NEW packages will be installed:
  binfmt-support winbind wine 
0 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/9669kB of archives. After unpacking 60.8MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
dpkg: failed to open package info file `/var/lib/dpkg/available' for reading: No such file or directory
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: failed to open package info file `/var/lib/dpkg/available' for reading: No such file or directory
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
jimbo@Monster:~$ 

```


???:confused:???

---

### Post by gjoellee on 2008-07-27
try download and install a .deb package instead: [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

---

### Post by morbid_bean on 2008-07-27
Great i fixed it....

sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available
  from [http://ubuntuforums.org/archive/index.php/t-389997.html](http://ubuntuforums.org/archive/index.php/t-389997.html)

---

### Post by marcisim on 2012-02-04
Neither of your solutions worked for me. 

It was fine with [this]("http://forums.linuxmint.com/viewtopic.php?f=34&t=70888"):

```
sudo dpkg --clear-avail && sudo apt-get update
```

):P

---

