---
title: "mysql-server won't install on ubuntu 6.04"
date: 2009-06-25
forum: Installation &amp; Upgrades
---

### Post by asmith393 on 2009-06-25
New to linux- have installed php5 and apache, but having trouble w/ mysql.

Any ideas? Thanks

Setting up mysql-server-5.0 (5.0.51a-3ubuntu5.1) ...
/etc/lsb-base-logging.sh: line 84: INITOUTPUT: unbound variable
invoke-rc.d: initscript mysql, action "stop" failed.
/etc/lsb-base-logging.sh: line 84: INITOUTPUT: unbound variable
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by quixote on 2009-06-26
Are you sure you're on version 6.04?  Dapper Drake was 6.06, and came out in 2006.  Or do you mean 9.04, Jaunty?  If so, you may want to edit your subject line, since that's likelier to bring someone in who can answer your question properly. 

I pretty hopeless at mysql myself, but I do have to use it both for my wordpress blog and moodle course software.  One red flag is that it's telling you that you have unmet dependencies.  Have you run```
sudo dpkg --configure -a
```That should fix all broken packages, not just mysql.  (The command "man dpkg" in the terminal brings up the info on how to do all kinds of things with dpkg.)

What I do is follow the instructions here: [http://maketecheasier.com/setting-up-a-lamp-server-in-ubuntu-hardy-heron/2008/08/06](http://maketecheasier.com/setting-up-a-lamp-server-in-ubuntu-hardy-heron/2008/08/06) to the letter when trying to install server software (apache, php, mysql).  Otherwise I tend to select the wrong kind of mysql in synaptic and wind up with the same kind of problem you have.

---

