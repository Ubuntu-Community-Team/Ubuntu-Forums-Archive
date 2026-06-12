---
title: "ADVANCED APT: avoid a package install to downgrade another"
date: 2009-09-10
forum: Installation &amp; Upgrades
---

### Post by Nokao on 2009-09-10
Hi ...
I'm trying to install phpmyadmin, but it asks me to downgrade from mysql-server-5.1 to mysql-server-5.0.

In a "virtual snapshot" I continued, blocked apt, and resolved with:
apt-get install mysql-server-5.1
apt-get -f install
And that resolved everything.

But in the "real machine" I would like to find a better solution.
How do I install a package avoiding a downgrade like that?

---

