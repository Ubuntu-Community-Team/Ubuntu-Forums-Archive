---
title: "apt(itude) fu: installed package version history?"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by jeffk on 2009-02-18
Yesterday I update my server's postgresql to postgresql-8.3.6-0ubuntu8.10. The pg_dump plaintext schema ordering changed, so I have unwanted diff artifacts between my Gentoo development machine.

Gentoo's postgresql is 8.3.5, so this would be the obvious reason, but I need to confirm that before yesterday's update, Ubuntu was on 8.3.5 too.

How do I do that with apt and or aptitude?

Also, is there an aptitude switch that will show the full package version number in 'aptitude search'?

Thanks.

---

### Post by bapoumba on 2009-02-18
You can use the show option:
```
bapoumba@SonyBlue:~$ aptitude show postgresql
Package: postgresql
State: not installed
Version: 8.3.6-0ubuntu8.04
Priority: optional
Section: misc
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 266k
Depends: postgresql-8.3
Description: object-relational SQL database (latest version)
 PostgreSQL is a fully featured object-relational database management system.
 It supports a large part of the SQL standard and is designed to be extensible
 by users in many aspects.  Some of the features are: ACID transactions, foreign
 keys, views, sequences, subqueries, triggers, user-defined types and functions,
 outer joins, multiversion concurrency control.  Graphical user interfaces and
 bindings for many programming languages are available as well. 
 
 This package always depends on the latest available database server for
 PostgreSQL.

```

Aptitude log is in /var/log/aptitude. Older actions are stored in .gz files in /var/log.

From [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
you can browse the changelog : [http://changelogs.ubuntu.com/changelogs/pool/main/p/postgresql-8.3/postgresql-8.3_8.3.4-2.2/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/p/postgresql-8.3/postgresql-8.3_8.3.4-2.2/changelog)

---

