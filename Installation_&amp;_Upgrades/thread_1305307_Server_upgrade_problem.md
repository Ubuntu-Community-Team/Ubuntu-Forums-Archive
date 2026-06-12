---
title: "Server upgrade problem"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by digitalchild on 2009-10-29
Hi all, 

today I upgraded, probably as many of you, my Ubuntu server via SSH. 

I losed connection during the upgrade and when I connected back to my linux box I tried to restore the installation. 

Now everything is upgraded, except for the MySQL databases: i noticed that the upgrade process has uninstalled version 5.0 and try to install 5.1, but it fails. 

Here is the output of update. 

```

apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up mysql-server-5.1 (5.1.37-1ubuntu5) ...
 * Stopping MySQL database server mysqld                                                                                                              [ OK ] 
Warning: found usr.sbin.mysqld in /etc/apparmor.d/force-complain, forcing complain mode
 * Starting MySQL database server mysqld                                                                                                              [fail]
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.1 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.1; however:
  Package mysql-server-5.1 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 mysql-server-5.1
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

Do you know how can I fix that?

Thanks 

digitalchild

---

### Post by DoctorLard on 2009-11-01
I get the same thing - I'm trying to see if there's anything in the launchpad bugs.

---

### Post by DoctorLard on 2009-11-01
The problem for me is when attempting to start MySQL it complains that it can't find the mysql.plugins table, and suggests running mysql_upgrade to fix it. Which of course fails because it can't find the local mysql server, because it won't start. It's this sort of shenanigans that reminds me why I use PostgreSQL.

[https://bugs.launchpad.net/mysql-server/+bug/444349](https://bugs.launchpad.net/mysql-server/+bug/444349)

---

### Post by intoxination on 2009-11-05
What I ended up doing was running mysqld straight from the command line so I could get the startup output. It turns out that in my.cnf there as skip-bdb, which is now history and it failed on that. I got rid of that line and mysql started fine then I was able to do the mysql_upgrade. All is well now.

---

### Post by defaria on 2009-11-14
I don't have any skip-bdb in my.cnf so that workaround doesn't work for me.

HELP! I need MySQL to be running!

---

