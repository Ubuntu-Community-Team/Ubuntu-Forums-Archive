---
title: "Karmic Postgis Problems"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by Davepar on 2009-11-01
I'm having quite a bit of trouble getting Postgis installed on Karmic. There seems to be two Postgis packages, postgis and postgresql-8.3-postgis. Since I installed postgresql, which installed version 8.4, I assume the plain postgis package is the one I should use.

The problem is that there should be a postgis.sql or lwpostgis.sql installed somewhere under /usr/share for setting up the special Postgis magic on a database. It's nowhere to be found after I installed postgis.

Any help appreciated.

Thanks,
Dave

---

### Post by ricardogsilva on 2009-11-01
Hello Dave
I am about to install postgresql and postgis on my laptop with karmic too. I did some googling after you brought up the subject and couldn't find a solution...

I think i'll stick with postgres 8.3 for now

If you manage to solve it please report back

---

### Post by Davepar on 2009-11-01
I ended up going back to PostgreSQL 8.3 as well. Here are the steps I used, which also include setting up Django and GeoDjango:
[http://pastebin.com/f3f292e7b](http://pastebin.com/f3f292e7b)

Dave

---

### Post by rfugger on 2010-01-04
Here's a postgis package for postgresql 8.4:

[http://trac.osgeo.org/postgis/attachment/wiki/UsersWikiPostgisOnUbuntu/postgis_1.4.1-1_i386.deb](http://trac.osgeo.org/postgis/attachment/wiki/UsersWikiPostgisOnUbuntu/postgis_1.4.1-1_i386.deb)

---

### Post by auspex on 2010-01-10
> **rfugger said:**
> Here's a postgis package for postgresql 8.4:

[http://trac.osgeo.org/postgis/attachment/wiki/UsersWikiPostgisOnUbuntu/postgis_1.4.1-1_i386.deb](http://trac.osgeo.org/postgis/attachment/wiki/UsersWikiPostgisOnUbuntu/postgis_1.4.1-1_i386.deb)

Hmm.  I thought that didn't contain postgis.sql, either, but I guess I didn't look hard enough.

Anyway, I downloaded the 8.4 versions of postgis and postgresql-8.4-postgis from lucid:
[http://mirrors.kernel.org/ubuntu/pool/universe/p/postgis/postgresql-8.4-postgis_1.4.0-2_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/p/postgis/postgresql-8.4-postgis_1.4.0-2_i386.deb)

---

