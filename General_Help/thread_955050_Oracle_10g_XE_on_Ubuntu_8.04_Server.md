---
title: "Oracle 10g XE on Ubuntu 8.04 Server"
date: 2008-10-21
forum: General Help
---

### Post by imagodei on 2008-10-21
Hello!

I'm having problem with installing and configuring Oracle 10g XE database.

I downloaded **deb** package from Oracle's site and I installed it using **dpkg -i**.

During installation there were minor errors, I can provide specifics if you think they might be of any use. However, the problem now is I cannot login via sqlplus console tool. I keep getting error:

```
Enter user-name: system
Enter password:
ERROR:
ORA-01034: ORACLE not available
ORA-27101: shared memory realm does not exist
Linux Error: 2: No such file or directory
```

Note that I haven't created any DB yet. I'm only following the installation tutorial, and there is a step in the tutorial, that suggests logging on to default XE database.

There are more problems: pfile and spfile aren't even present for the default (XE) DB or they have wrong name. Also the alert.log file just doesn't get created, so I can't provide you with details on error.

I've been asking the same question over on Oracle forums, but so far the guys there couldn't help me.

Do you have any ideas? Does Ubuntu 8.04 even support Oracle 10g XE?

Thank you for your help!

---

### Post by dgavenda on 2008-11-18
use: sqlplus /nolog

---

### Post by 1eyedjacks on 2009-07-06
Hi:

For anyone having difficulty configuring Oracle 10g Express on (hardy heron) Ubuntu Linux, what I did is very simple and it worked.

1) Use Synaptic Package Manager to download the 'deb' file option at Oracle 10g download site for Linux

2) Install with all the defaults (in fact, my configuration only asked for my sudo root password to install everything)

3) Look in your 'Applications' menu, and see Oracle available.

4) Try to open the database homepage, and if you are using Firefox, you will most likely get an error.

5) open a terminal, and type: sudo /etc/init.d/oracle-xe configure

6) enter the defaults in square brackets, 8080, 1521, etc., unless you know better

7) enter the Oracle SYSTEM password that you like and confirm.

8)  Allow a few minutes for the configuration to complete.

9)  Try to re-open the database login page.  At this point, it worked for me.  Good luck.

---

### Post by Waappu on 2009-07-08
Hi

Maybe you uninstall and start for begin. Follow these guides.

[https://help.ubuntu.com/community/Oracle10g](https://help.ubuntu.com/community/Oracle10g)
[http://www.oracle.com/technology/tech/linux/install/xe-on-kubuntu.html](http://www.oracle.com/technology/tech/linux/install/xe-on-kubuntu.html)
[http://www.debian-administration.org/articles/430](http://www.debian-administration.org/articles/430)

---

