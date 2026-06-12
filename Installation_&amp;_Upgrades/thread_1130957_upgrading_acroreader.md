---
title: "upgrading acroreader?"
date: 2009-04-20
forum: Installation &amp; Upgrades
---

### Post by bodhidharma on 2009-04-20
Anyone having this problem?  In update manager for the last
few days, I get notification that it wants to upgrade
acroread, it downloads, works on the installation, then
an error window comes up saying:

E: /var/cache/apt/archives/acroread_9.1.0-7intrepid1_i386.deb: trying to overwrite `/usr/share/man/man1/acroread.1.gz', which is also in package acroread-debian-files


Any ideas?

Thanks!

---

### Post by krgp on 2009-04-23
Same problem upgrading to latest acroread / acrobat. Constant message from update manager, and this is the error when I try to upgrade in terminal:

The following packages will be upgraded:
  acroread
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/63.4MB of archives.
After this operation, 81.1MB of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 180665 files and directories currently installed.)
Preparing to replace acroread 8.1.3-0medibuntu0.8.10.2 (using .../acroread_9.1.0-7intrepid1_i386.deb) ...
Unpacking replacement acroread ...
dpkg: error processing /var/cache/apt/archives/acroread_9.1.0-7intrepid1_i386.deb (--unpack):
 trying to overwrite `/usr/share/man/man1/acroread.1.gz', which is also in package acroread-debian-files
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/acroread_9.1.0-7intrepid1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any ideas? This seems to be a common problem, but I can find a SOLVED thread.

---

