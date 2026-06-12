---
title: "Preseeding PostgreSQL 8.2"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by blafrisch on 2009-05-18
I'm customizing the Ubuntu installer for a Hardy based install of my custom package set.  Right now I have everything working except for PostreSQL version 8.2 and I can't figure out how to preseed it so this message doesn't pop up.  The message I get is a red window with this:

> 
Description: Obsolete major version 8.2
The PostgreSQL version 8.2 is obsolete, but the server
or client packages are still installed. Please install the latest packages
(postgresql-8.3 and postgresql-client-8.3) and upgrade the
existing 8.2 clusters with pg_upgradecluster (see manpage).
Please be aware that the installation of postgresql-8.2 will
automatically create a default cluster 8.3/main. If you want to upgrade
the 8.2/main cluster, you need to remove the already existing 8.3
cluster (pg_dropcluster --stop 8.3 main, see manpage for
details).
The old server and client packages are no longer supported. After the
existing clusters are upgraded, the postgresql-8.2 and
postgresql-client-8.2 packages should be removed.
Please see /usr/share/doc/postgresql-common/README.Debian.gz for details.


The options are <Go Back> and <Continue>.  If I select Continue then the install finishes as I expect it to, but I just can't figure out how to preseed past this step.  Any ideas?

No, I can't upgrade the packages to PostgreSQL 8.3

---

