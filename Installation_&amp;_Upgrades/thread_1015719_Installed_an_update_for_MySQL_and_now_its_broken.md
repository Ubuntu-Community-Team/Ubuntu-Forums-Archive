---
title: "Installed an update for MySQL and now its broken"
date: 2008-12-19
forum: Installation &amp; Upgrades
---

### Post by richard270384 on 2008-12-19
Hi all,

I installed an update a couple of days ago for MySQL using the update manager.

Now MySql doesn't work (which is a complete pain in the ***). I've just finished work for the year and was looking forward to building a new website.

Anyway, the error I'm getting is: ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

Now, my laptop has an overheating problem and it is quite possible that the update never completed (which caused the problem) because my laptop overheated.

But I also noticed that my hard drive was full (which could also have caused some problems).

I was thinking it might be best to uninstall MySQL and re-install it again. What is the best way to go about doing that?

Or do you have another suggestion?

Cheers,
Richard

---

### Post by Liviu-Theodor on 2008-12-19
Probably you have run out of HDD space and MySQL did not install completely. Maybe it is not the update to blame. I think in your situation the best thing to do is: uninstall MySQL, make room on the hdd (delete files in trash, in /tmp, various files no longer necessary, uninstall programs you don't use, or even edit your partitions), than reinstall MySQL. Sometimes when the the HDD is full, the only solution is a LiveCD.

---

### Post by richard270384 on 2008-12-19
Thanks. That was what I thought I would need to do. Whats the easiest way to remove mysql?

---

### Post by richard270384 on 2008-12-20
Problem solved. Interestingly enough, I cleared some space, and restarted my laptop. MySQL worked fine after that.

---

