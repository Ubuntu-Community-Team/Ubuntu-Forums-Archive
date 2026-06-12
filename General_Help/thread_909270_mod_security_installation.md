---
title: "mod security installation"
date: 2008-09-03
forum: General Help
---

### Post by chamkaran on 2008-09-03
Hi Guys
i am new in ubuntu.
i successfully installed the apache2 with the command sudo apt-get install apache2, but getting the folloing error during installation of mod security with the command sudo apt-get install libapache2-mod-security2.
The error is : "E: Couldn't find package mod-security".
I also tried with sudo dpkg -i mod-security.2.5.5 after downloading the package.but gets the following error
dpkg-split: error reading modsecurity-apache_2.5.5: Is a directory
dpkg: error processing modsecurity-apache_2.5.5 (--install):
subprocess dpkg-split returned error exit status 2
Errors were encountered while processing:
modsecurity-apache_2.5.5
Your help will be much appreciated.
Regards

---

### Post by pipemartinm on 2009-04-30
Any word on this? I get the same problem (or similar)
```

root@server:/etc/apt# apt-get install libapache-mod-security
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package libapache-mod-security is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libapache-mod-security has no installation candidate
root@psnmc-nms-pr-01:/etc/apt#


```

---

### Post by muramura on 2009-05-15
Same problem.

 "sudo apt-get install libapache2-mod-security"
returns:
 "Couldn't find package libapache2-mod-security"

Advice anyone?

---

### Post by albinootje on 2009-05-15
Which Ubuntu release are you using ?
See here for the options on the various Ubuntu releases :
[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=mod+security](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=mod+security)

---

### Post by muramura on 2009-05-15
Ubuntu 8.04.2

I'm still not linux proficiant enough to make use of that page you sent. :oops:

---

### Post by albinootje on 2009-05-16
> **muramura said:**
> Ubuntu 8.04.2

I'm still not linux proficiant enough to make use of that page you sent. :oops:

Okay :)

From the link I gave, you can see that mod_security as a package is only available for Ubuntu Dapper, Jaunty and Karmic, and.. unfortunately for you not for Ubuntu Hardy.

---

