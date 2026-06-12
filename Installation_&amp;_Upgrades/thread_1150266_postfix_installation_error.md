---
title: "postfix installation error"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by jjt288 on 2009-05-05
Hi guys,

I'm setting up my new Jaunty server box and I cannot get postfix to install correctly.

When I run apt-get, I get this (look at the end):

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  procmail postfix-mysql postfix-pgsql postfix-ldap postfix-pcre sasl2-bin resolvconf postfix-cdb mail-reader ufw
The following NEW packages will be installed:
  postfix
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1219kB of archives.
After this operation, 3006kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package postfix.
(Reading database ... 21022 files and directories currently installed.)
Unpacking postfix (from .../postfix_2.5.5-1.1_i386.deb) ...
Setting up postfix (2.5.5-1.1) ...
Creating /etc/postfix/dynamicmaps.cf
Adding tcp map entry to /etc/postfix/dynamicmaps.cf
setting myhostname: JT1
setting alias maps
setting alias database
mailname is not a fully qualified domain name.  Not changing /etc/mailname.
setting destinations: terenz.io, johnterenzio.net, theemoticon.com, tapin.com, livtravel.com, tweehicle.com, localhost, localhost.localdomain, localhost
setting relayhost: 
setting mynetworks: 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
setting mailbox_size_limit: 0
setting recipient_delimiter: +
setting inet_interfaces: all
setting inet_protocols: ipv4
WARNING: /etc/aliases exists, but does not have a root alias.

Postfix is now set up with a default configuration.  If you need to make 
changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
 * Stopping Postfix Mail Transport Agent postfix
   ...done.
 * Starting Postfix Mail Transport Agent postfix
postfix: fatal: /etc/postfix/postfix-script: No such file or directory
   ...fail!
invoke-rc.d: initscript postfix, action "restart" failed.
dpkg: error processing postfix (--configure):
 subprocess post-installation script returned error exit status 1
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)

Thanks in advance for any help.
jjt

---

