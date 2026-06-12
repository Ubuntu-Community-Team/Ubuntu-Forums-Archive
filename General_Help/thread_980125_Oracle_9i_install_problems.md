---
title: "Oracle 9i install problems"
date: 2008-11-12
forum: General Help
---

### Post by schwaber on 2008-11-12
Hello,

I'm hoping someone might be able to help me out.  I'm running 2.6.24-19-server (64 bit) and trying to install Oracle 9i 64 bit.  I downloaded the installation files from oracle's site and unpacked them into folders disk1, disk2 and disk3.  I followed everything in this tutorial: [http://xlayn.blogspot.com/2007/07/oracle-10gr2-on-ubuntu-server-704.html](http://xlayn.blogspot.com/2007/07/oracle-10gr2-on-ubuntu-server-704.html) up to the Step 9.  When i try to run the installer I get this error:

oracle@server:/oracle9i/disk1$./runInstaller -ignoreSysPrereqs
./runInstaller: 62: Syntax error: word unexpected (expecting ")")

When I go into the disk1/install/linux directory to try to run the installer there I get:
oracle@server:/oracle9i/disk1/install/linux$./runInstaller -ignoreSysPrereqs
bash: ./runInstaller: No such file or directory

But I can see the file when I ls.

I can't figure out why the installer won't run.

Any help would be appreciated.
Thanks!

---

### Post by ateixeira on 2012-04-12
Hello,

I'm experiencing the same problem, I'm trying to install Oracle 9i on Ubuntu server 11.10, and I've followed this tutorial [https://help.ubuntu.com/community/Oracle9i](https://help.ubuntu.com/community/Oracle9i) and I also get the same ./runInstaller: 62: Syntax error: word unexpected (expecting ")") error.

Thank you for your help.

Cheers,
André

---

