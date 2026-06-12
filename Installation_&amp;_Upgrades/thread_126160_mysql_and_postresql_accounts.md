---
title: "mysql and postresql accounts"
date: 2006-02-05
forum: Installation &amp; Upgrades
---

### Post by browneyedgirl65 on 2006-02-05
Hi, all...I have successfully installed both of these databases on my system, but I have a question that applies to both.

In each case an account (/var/lib/mysql, var/lib/postgresql) was created as the "owner" or "root" of the database server.  OK, all well and good, but what are their passwords?  I would like to change the default passwords for these accounts.  I can get into them via sudo su - of course, but it seems a security leak.

If ther'es a place to go where this information is listed, I would like to know where that is.

One thing I"m also wondering is if these aren't "real" accounts with actual passwords since they aren't in /home?

As a sidenote, I've looked at /etc/passwds but there's isn't much info there.  What is the passwd structure these days?  I go back to SunOs systems, so I'm not up on the way the linux installations are organized.

Thanks in advance for replies, suggestions, and answers...

--BEG

---

