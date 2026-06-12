---
title: "Installing CVS on Ubuntu"
date: 2009-08-17
forum: Installation &amp; Upgrades
---

### Post by sreddy64 on 2009-08-17
I configured a virtual machine with ubuntu 2.6.24-19 and wanted to have CVS. 
I downloaded the CVS package cvs-1.12.9 and tried to run the command ./configure, I am getting the following error message
 
Configure error: C Preprocessor "/lib/cpp" fails sanity check . Check config.log
 
When I check config log file, I see lot of error messages like
/usr/include/bits/local_lim.h No such file or directory
 
 
Thanks in adavance for the help
Vizardo.

---

### Post by Partyboi2 on 2009-08-18
Hi, cvs is in the Ubuntu repos, so you should be able to install with
```
sudo apt-get install cvs
```

---

### Post by sreddy64 on 2009-08-18
Thanks for your reply. The machine which  ubuntu is running not connected to internet and it is not possible to put this one on the internet. Is there any other way of downloading and installing?
 
Thanks

---

### Post by Partyboi2 on 2009-08-19
You can go [[COLOR=Blue]here[/COLOR]]("http://packages.ubuntu.com/search?keywords=cvs&searchon=names&suite=all&section=all") and download the cvs deb package,t hen double click to start the install process, you may need to install some other dependencies for cvs which can be found [[COLOR=Blue]here[/COLOR]]("http://packages.ubuntu.com/").

---

