---
title: "Apt-get reports success yet files aren't installed"
date: 2009-09-16
forum: Installation &amp; Upgrades
---

### Post by raemike on 2009-09-16
Trying to get apache2 to parse php files with Ubuntu 9.  In CentOS this is automatic, it is a joke of a process here.  In any case, I look in /etc/apache2/ and php module is not present:

```
/etc/apache2/mods-enabled# ls
alias.conf            authz_user.load  dir.conf          setenvif.conf
alias.load            autoindex.conf   dir.load          setenvif.load
auth_basic.load       autoindex.load   env.load          status.conf
authn_file.load       cgid.conf        mime.conf         status.load
authz_default.load    cgid.load        mime.load
authz_groupfile.load  deflate.conf     negotiation.conf
authz_host.load       deflate.load     negotiation.load

```I look in available and it is not present either.

I try to install from apt-get

> sudo apt-get install libapache2-mod-php5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libapache2-mod-php5 is already the newest version.
The following packages were automatically installed and are no longer required:
  libapparmor1 liburi-perl libapparmor-perl libfont-afm-perl libmailtools-perl
  libhtml-parser-perl librpc-xml-perl libxml-parser-perl libhtml-format-perl
  libhtml-tree-perl libwww-perl libhtml-tagset-perl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.

The net result is I can't get PHP files to be properly interpreted by Apache.

---

