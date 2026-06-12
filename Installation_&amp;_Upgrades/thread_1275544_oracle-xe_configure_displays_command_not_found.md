---
title: "oracle-xe configure displays command not found"
date: 2009-09-25
forum: Installation &amp; Upgrades
---

### Post by dhd1956 on 2009-09-25
As displayed below, I am unable to get ubuntu to recognize the oracle-xe configure command.

Here's the tail end of the install followed by my attempt to configure...

Any ideas what is missing?


Setting up oracle-xe (10.2.0.1-1.1) ...
Executing Post-install steps...

-e You must run '/etc/init.d/oracle-xe configure' as the root user to configure the database.

dave@dave-desktop:~$ sudo etc/init.d/oracle-xe configure
[sudo] password for dave:
sudo: etc/init.d/oracle-xe: command not found

---

### Post by Waappu on 2009-09-26
Hi,

Try
```
sudo /etc/init.d/oracle-xe configure
```

---

### Post by dhd1956 on 2009-09-26
That's the command I used. Just for good measure I copies and pasted your suggestion and got the same results. It doesn't recognize what oracle-xe is. The file contains what looks like the right information. I have included the beginning of the file below...

dave@dave-desktop:/etc/init.d$ sudo /etc/init.d/oracle-xe configure
[sudo] password for dave:
sudo: /etc/init.d/oracle-xe: command not found
dave@dave-desktop:/etc/init.d$ cd /etc/init.d
dave@dave-desktop:/etc/init.d$ head oracle-xe
#!/bin/bash
#
#
# chkconfig: 2345 80 05
# description: This is a program that is responsible for taking care of
# configuring the Oracle Database 10g Express Edition and its associated
# services.
#
# processname: oracle-xe
# Red Hat or SuSE config: /etc/sysconfig/oracle-xe
dave@dave-desktop:/etc/init.d$

---

### Post by dhd1956 on 2009-09-26
more clues.

I searched some more and found the following command that at least didn't result in 'command not found'.

dave@dave-desktop:/etc/init.d$ sudo sh /etc/init.d/oracle-xe configure
Oracle Database 10g Express Edition is already configured

So then I tried:

dave@dave-desktop:/etc/init.d$ sudo sh /etc/init.d/oracle-xe restart
Oracle Database 10g Express Edition is not configured.  You must run
'/etc/init.d/oracle-xe configure' as the root user to configure the database.
dave@dave-desktop:/etc/init.d$

---

### Post by Waappu on 2009-09-27
Hi,

I do not know.
Try uninstall and then reinstall
[https://help.ubuntu.com/community/Oracle10g](https://help.ubuntu.com/community/Oracle10g)
[http://www.debian-administration.org/articles/430](http://www.debian-administration.org/articles/430)
[http://www.oracle.com/technology/tech/linux/install/xe-on-kubuntu.html](http://www.oracle.com/technology/tech/linux/install/xe-on-kubuntu.html)

---

### Post by dhd1956 on 2009-09-27
Thanks for the web sites.  From the first site I found the command: sudo aptitude purge oracle-xe which allowed me to start over and now the configure command worked and I have oracle installed properly.

thanks again...

---

