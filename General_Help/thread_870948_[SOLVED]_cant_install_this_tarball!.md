---
title: "[SOLVED] cant install this tarball!"
date: 2008-07-26
forum: General Help
---

### Post by mikedemario17 on 2008-07-26
y cant i install it.......
> mike@mike-desktop:~$ su
Password: 
root@mike-desktop:/home/mike# cd  recordmydesktop-0.3.7.3
root@mike-desktop:/home/mike/recordmydesktop-0.3.7.3# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
root@mike-desktop:/home/mike/recordmydesktop-0.3.7.3# 


---

### Post by youthforlinux on 2008-07-26
Try installing the build-essential package:

```
sudo aptitude install build-essential
```

---

### Post by spiderbatdad on 2008-07-26
normally ./configure and make are not run as root.

```
./configure
make
sudo make install
```

You should not use su for root access. Instead use:```
sudo -i
``` And that is not needed for compiling programs from source.

Also recordmydesktop is in synaptic package manager. So the best way to install that program is:
```
 sudo apt-get install recordmydesktop gtk-reordmydesktop
```

---

### Post by logos34 on 2008-07-26
why don't you save yourself some trouble and use the .deb--it's in the repos 

enable universe repo first

system>admin>software sources>**universe**

sudo apt-get install recordmydesktop

---

### Post by mikedemario17 on 2008-07-26
i installed it... useing synaptic package manager...but i want to know how to install a tarball...(.tar) coz have the stuff for linux is that. deb. are hard to find for me that is

---

### Post by spiderbatdad on 2008-07-26
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by mikedemario17 on 2008-07-26
very good site ^

---

### Post by logos34 on 2008-07-26
If you have to go the tarball route, I'd recommend using the checkinstall + auto-apt method, that way you can keep track of and easily remove installed software.  It's always worked great for me.

[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

enjoy

---

### Post by mikedemario17 on 2008-07-26
thanks

---

