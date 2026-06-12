---
title: "SVN From Source"
date: 2009-04-07
forum: Installation &amp; Upgrades
---

### Post by wiggsfly on 2009-04-07
Hello, I'm not sure if this is the correct forum, but I am trying to install SVN from source and am having an issue. Namely, I cannot seem to enable support for BDB. I've installed the following packages via apt: apache2, libapache2-svn, libneon27-dev, libdb4.7-dev. 

If I simply run ./configure from source I get the message that it cannot find Berkeley DB and that the makefile has been created without it. If I enter 

./configure --with-berkeley-db=db.h:/usr/local/include/db4.7:/usr/local/lib/db4.7:db-4.7

I can complete the configuration successfully but when I run make it fails with:

libtool: link: cannot determine absolute directory name of `db-4.7'

Any suggestions? I must compile from source for a class project and I cannot seem to get by this part.

Thanks!

---

