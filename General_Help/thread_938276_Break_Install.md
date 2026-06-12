---
title: "Break Install"
date: 2008-10-04
forum: General Help
---

### Post by victor9191 on 2008-10-04
I get this error when i try to install pptp config for my VPN. I tried lots of commands to fix. heres the error.

victor@(none):~$ sudo apt-get install --fix-missing
sudo: unable to resolve host (none)
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up postgresql-8.3 (8.3.3-0ubuntu0.8.04) ...
 * Starting PostgreSQL 8.3 database server                                       * The PostgreSQL server failed to start. Please check the log output:
2008-10-04 17:29:48 CDT LOG:  could not load root certificate file "root.crt": no SSL error reported
2008-10-04 17:29:48 CDT DETAIL:  Will not verify client certificates.
2008-10-04 17:29:48 CDT LOG:  could not translate host name "localhost", service "5432" to address: Name or service not known
2008-10-04 17:29:48 CDT WARNING:  could not create listen socket for "localhost"
2008-10-04 17:29:48 CDT FATAL:  could not create any TCP/IP sockets
                                                                         [fail]
invoke-rc.d: initscript postgresql-8.3, action "start" failed.
dpkg: error processing postgresql-8.3 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of postgresql:
 postgresql depends on postgresql-8.3; however:
  Package postgresql-8.3 is not configured yet.
dpkg: error processing postgresql (--configure):
 dependency problems - leaving unconfigured
Setting up secvpn (2.21) ...
Starting Monitor Daemon for Secure Virtual Private Network: cp: cannot stat `/etc/inittab': No such file or directory
invoke-rc.d: initscript secvpnmon, action "start" failed.
dpkg: error processing secvpn (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 postgresql-8.3
 postgresql
 secvpn
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

