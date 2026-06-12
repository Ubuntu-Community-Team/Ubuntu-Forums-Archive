---
title: "libnet-ssleay-perl"
date: 2009-10-19
forum: Installation &amp; Upgrades
---

### Post by handsomechap on 2009-10-19
Hello I am a bit of a linux command line noob, I've got ubuntu 9.04 installed on a server and want to install [webmin]("http://www.webmin.com/"), I've downloaded the latest version but when i try to run the installer I get the following error:

```

Unpacking webmin (from webmin_1.490_all.deb) ...
dpkg: dependency problems prevent configuration of webmin:
 webmin depends on libnet-ssleay-perl; however:
  Package libnet-ssleay-perl is not installed.
 webmin depends on libauthen-pam-perl; however:
  Package libauthen-pam-perl is not installed.
 webmin depends on libio-pty-perl; however:
  Package libio-pty-perl is not installed.
 webmin depends on libmd5-perl; however:
  Package libmd5-perl is not installed.
dpkg: error processing webmin (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 webmin

```so i try:

```

:~# sudo apt-get install libnet-ssleay-perl
Reading package lists... Done
Building dependency tree... Done
Package libnet-ssleay-perl is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libnet-ssleay-perl has no installation candidate

```How can i get these packages?

Thanks in advance :-]

---

### Post by philif on 2009-10-20
just run
 
dpkg -i webmin_1.441_all.deb
( yes errors no problem ignore it)
 
apt-get install -f
 
and it works.
 
If you have a problem with the login in firefox then change the settings like below.
 
Firefox:
go to Edit -> Preferences -> Advanced Button -> Encryption Tab
View Certificates -> [[COLOR=blue][FONT=Verdana][FONT=Verdana]Servers[/FONT][/FONT][/COLOR]]("http://www.linuxquestions.org/questions/#") Tab
Add Exception -> Enter "https://localhost:10000"
Get Certificate -> Confirm Security Exception
Click Ok.

---

