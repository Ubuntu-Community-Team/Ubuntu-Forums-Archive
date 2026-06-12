---
title: "Upgrading a server to 9.04"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by Znupi on 2009-05-03
[ Offtopic: There should be a 'server' prefix for new threads ]

My brother has a server running Ubuntu 8.10 (64bit), which he lets me use, too. He uses it mainly for Apache + MySQL + PHP (MySQL is **really** important).
I would like to upgrade it to 9.04, mainly for Python 2.6 (I need it for a new application I'm working on) but also because I like being on the bleeding edge :D.
Now, we have a somewhat peculiar setup (MySQL stores its databases on a special partition, for which we had to do some workarounds). Anyway, I was wondering if there are any problems I would run in to if I upgraded. Will MySQL / Apache / PHP configurations be changed in any way? We have quite a few virtual hosts in Apache that I would really not enjoy losing. Also, is there any chance MySQL would be upgraded in such a way that it will not recognize the old databases?

Thanks :)

---

### Post by Znupi on 2009-05-04
Bump (wow, never had to bump around here before.. except on the bump thread! :D)

---

### Post by ptn107 on 2009-05-04
I have not had any apache2/mysql problems since I upgraded my server two weeks ago.  Make sure the update-manager-core package is installed, do a sudo do-release-upgrade, and away you go.

---

