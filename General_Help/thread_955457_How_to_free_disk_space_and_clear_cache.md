---
title: "How to free disk space and clear cache"
date: 2008-10-22
forum: General Help
---

### Post by waseeman on 2008-10-22
Hi,

Is it safe to delete files and folders in /var/cache?

I'm a novice Linux user and I have a linux server running kernel 2.6.18-6-amd64, and with apache2 running on it. On it, I have a website with about 60GB of information (music downloads).

The hardrive is full 100%. The cache gets full considerabely very fast, about 10 to 20GB in 2-3 months. I cleared the cache in /var/cache/apt using get-apt autoclean but that was not near enough.

Can I delete the content of:
/var/cache/apache2
/var/cahce/cups
/var/cahce/locate
/var/cache/man
/var/cache/gnome-system-tools
/var/cache/dictionaries-common
/var/cache/debconf
/var/cache/setup-tools-backend

?

---

### Post by jnorthr on 2008-10-22
There may be a lot of log files hanging around in /var/log as well that you can clear down. After a period of time, they are zipped into *.gz files for you to backup (or remove).  But if you have 60GB of data you need to seriously think of adding more storage (it's cheap now) or moving it to an auxiliary drive, as you will continue to run into this problem again.

---

### Post by waseeman on 2008-10-22
I agree and I intend to do so. Problem is that I need to find an immediate solution since this is causing the site to act extremely slow.

---

### Post by waseeman on 2008-10-22
Any more suggestion guys?

---

