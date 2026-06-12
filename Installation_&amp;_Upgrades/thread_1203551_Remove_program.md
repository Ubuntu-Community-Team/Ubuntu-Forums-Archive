---
title: "Remove program"
date: 2009-07-03
forum: Installation &amp; Upgrades
---

### Post by DutchManNL on 2009-07-03
Hi,

I formated my ubuntu server, i thought i installed the same ftp package but i didnt.
Now i am wondering how i can delete it.
I searched the net and i found the apt-get remove.... not good??

stef@LinuxServer:/etc/proftpd$ sudo apt-get install vsftpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  proftpd-basic: Depends: libcap1 but it is not going to be installed
                 Conflicts: ftp-server
  vsftpd: Depends: libcap1 but it is not going to be installed
          Depends: ssl-cert (>= 1.0-11ubuntu1) but it is not going to be installed
          Conflicts: ftp-server
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

So i thought remove fpt
This is what happend next:

stef@LinuxServer:/etc/proftpd$ sudo apt-get remove ftp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  proftpd-basic: Depends: libcap1 but it is not going to be installed
  ubuntu-standard: Depends: ftp
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
stef@LinuxServer:/etc/proftpd$ 


Cant figure it out anymore
Tnx

Stef

---

