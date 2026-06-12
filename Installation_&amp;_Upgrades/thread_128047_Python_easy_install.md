---
title: "Python easy_install"
date: 2006-02-10
forum: Installation &amp; Upgrades
---

### Post by WelterPelter on 2006-02-10
Hi. Trying into install the python package manager ([]("http://peak.telecommunity.com/DevCenter/EasyInstall#configuration-files"))
Running the installer py file on ubuntu, I get a consistant error message: ```
SystemExit: error: invalid Python installation: unable to open /usr/lib/python2.4/config/Makefile (No such file or directory)
```

Of course, I'm running the latest Python on Breezy that was set up by the installer and Python works fine. Actually, the problem is clear: the folder "config" doesn't exist in my python2.4 folder. 

Anyone else have a problem with this? What did you do?

---

### Post by Greg2 on 2006-02-10
You need to install the python2.4-dev package with synaptic or apt-get.

---

### Post by WelterPelter on 2006-02-10
Sure enough, that does the trick. 
Thanks! 
I just assumed that all the python extras were installed. 
.
.
.
*DUH.*

---

### Post by rbgCODE on 2006-07-31
> **WelterPelter said:**
> Sure enough, that does the trick. 
Thanks! 
I just assumed that all the python extras were installed. 
.
.
.
*DUH.*

What switches are you using when installing easy setup?

Did you download the ez_setup.py off their site?  what did you type to install it?  I am having problems getting it installed and would really like the help

---

