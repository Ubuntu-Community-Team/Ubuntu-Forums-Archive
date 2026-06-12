---
title: "Oki ML 490"
date: 2011-01-17
forum: Hardware
---

### Post by WilliamThrilliam on 2011-01-17
Hello,

I have a problem installing the manufacturer supplied Linux driver from oki.  I am running Ubuntu 10.10 x86_64.  I have also put in a request over at cups.org, but I haven't gotten a response.

Could someone test out the install script and see whats wrong?  It errors out saying it can't find some files that are clearly in the same directory.

Website:
[http://my.okidata.com/pp-ML490.nsf/openingdrivermenu?OpenFrameSet](http://my.okidata.com/pp-ML490.nsf/openingdrivermenu?OpenFrameSet)

Driver
[http://my.okidata.com/dsdownWeb.nsf/driverlookup/C32C08D11B9D7AA4852577A40054C462?OpenDocument](http://my.okidata.com/dsdownWeb.nsf/driverlookup/C32C08D11B9D7AA4852577A40054C462?OpenDocument)

Thank you!

---

### Post by WilliamThrilliam on 2011-01-20
The install script gives me this error:

user@ubuntu:~$ sudo /home/user/Downloads/dotmatrix/install.sh
[sudo] password for user: 
ls: cannot access ok*ppd*: No such file or directory
install.sh: ERROR: cannot find rastertookidotmatrix

---

### Post by WilliamThrilliam on 2011-01-20
The install script gives me this error:

user@ubuntu:~$ sudo /home/user/Downloads/dotmatrix/install.sh
[sudo] password for user: 
ls: cannot access ok*ppd*: No such file or directory
install.sh: ERROR: cannot find rastertookidotmatrix

---

### Post by WilliamThrilliam on 2011-01-20
The install script gives me this error:

user@ubuntu:~$ sudo /home/user/Downloads/dotmatrix/install.sh
[sudo] password for user: 
ls: cannot access ok*ppd*: No such file or directory
install.sh: ERROR: cannot find rastertookidotmatrix

---

### Post by WilliamThrilliam on 2011-01-20
Sorry for the duplicate posts, my internet was being goofy.

Anyway, I figured out my initial problem: I didn't cd into the directory, I'm such a n00b.  After I did that everything went smoothly except for actually adding the printer in printer settings.  Cups gave an "internal error" prompt and failed to add the print when I selected the ppd (this is through the gui method).

This is a bug, since entering a ppd in this way fails to add the printer to /etc/cups/ppd/ . So, I just went ahead and added my ppd to that file, and presto, everything now works.

---

