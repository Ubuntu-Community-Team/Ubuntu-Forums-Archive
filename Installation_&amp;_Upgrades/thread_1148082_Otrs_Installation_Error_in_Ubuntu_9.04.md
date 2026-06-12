---
title: "Otrs Installation Error in Ubuntu 9.04"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by raviproff on 2009-05-04
Hi

I tried to install otrs2 in ubuntu
I got below error msg, Please help me

```
root at ServerOSS:/home/ravi# apt-get install otrs2
Reading package lists... Done
Building dependency tree
Reading state information... Done
otrs2 is already the newest version.
The following packages were automatically installed and are no longer  
required:
pwgen mythtv-common mobile-broadband-provider-info gnome-themes-selected  
tango-icon-theme python-pkg-resources odt2txt python-rdflib
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up otrs2 (2.3.2-2) ...
dbconfig-common: writing config to /etc/dbconfig-common/otrs2.conf
*** WARNING: ucf was run from a maintainer script that uses debconf, but
the script did not pass --debconf-ok to ucf. The maintainer
script should be fixed to not stop debconf before calling ucf,
and pass it this parameter. For now, ucf will revert to using
old-style, non-debconf prompting. Ugh!

Please inform the package maintainer about this problem.
Replacing config file /etc/otrs/database.pm with new version
granting access to database otrs2 for otrs at localhost: already exists.
creating database otrs2: success.
verifying database otrs2 exists: success.
populating database via sql... done.
dbconfig-common: flushing administrative password
Module perl already enabled
ERROR: Module rewrite not properly enabled:  
/etc/apache2/mods-enabled/rewrite.load is a real file, not touching it
dpkg: error processing otrs2 (--configure):
subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
otrs2
E: Sub-process /usr/bin/dpkg returned an error code (1)
root at ServerOSS:/home/ravi#
```



Thanks,
Ravi

---

