---
title: "Upgrade issue"
date: 2008-11-04
forum: General Help
---

### Post by adam35413 on 2008-11-04
I run Ubuntu 7.10 server on my machine at home and thought it would be a good idea to update to at least 8.04 LTS.  However, when I went to do this by using the following command: 

sudo do-release-upgrade

I ended up getting an error after it had fully downloaded all the packages and started installing.  I was a very large trace back so I am not sure exactly where it happened at.  I figured upgrading was probably not going to be an option for me then.  However, when I went to use my webserver on this machine I was getting errors like: 

```
Can't do setuid (cannot exec sperl)
[Tue Nov 04 22:35:32 2008] [error] [client 192.168.1.5] Premature end of script headers: index.cgi

```

I tried to do an aptitude update, but that failed as well and aptitude recommended running dpkg --configure -a.  I tried running this command, but I errored out after a few seconds at

```
Setting up libpng12-0 (1.2.27-1) ...
Can't locate Pod/Usage.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/sbin/install-docs line 18.
Global symbol "$opt_rootdir" requires explicit package name at /usr/sbin/install-docs line 136.
Execution of /usr/sbin/install-docs aborted due to compilation errors.
dpkg: error processing libpng12-0 (--configure):
 subprocess post-installation script returned error exit status 9
dpkg: dependency problems prevent configuration of libhtml-tagset-perl:
 libhtml-tagset-perl depends on perl (>= 5.6.0-16); however:
  Package perl is not configured yet.
dpkg: error processing libhtml-tagset-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcupsimage2:
 libcupsimage2 depends on libpng12-0 (>= 1.2.13-4); however:
  Package libpng12-0 is not configured yet.
dpkg: error processing libcupsimage2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of liblaunchpad-integration1:
 liblaunchpad-integration1 depends on libgtk2.0-0 (>= 2.14.1); however:
  Version of libgtk2.0-0 on system is 2.12.0-1ubuntu3.
 liblaunchpad-integration1 depends on libpango1.0-0 (>= 1.21.6); however:
  Package libpango1.0-0 is not configured yet.
dpkg: error processing liblaunchpad-integration1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgpod-common:
 libgpod-common depends on libgpod3-nogtk (>= 0.6.0) | libgpod3 (>= 0.6.0); however:
  Package libgpod3-nogtk is not installed.
  Package libgpod3 is not configured yet.
dpkg: error processing libgpod-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcairo2:
 libcairo2 depends on libpng12-0 (>= 1.2.13-4); however:
  Package libpng12-0 is not configured yet.
dpkg: error processing libcairo2 (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.
Aborted (core dumped)

```

This was after a bunch of dependency warnings from dpkg as well.

Does anyone have any ideas?  I really don't want to have to reload the OS.

---

