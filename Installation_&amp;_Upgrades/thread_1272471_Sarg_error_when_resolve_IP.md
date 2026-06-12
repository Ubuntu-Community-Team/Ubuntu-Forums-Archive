---
title: "Sarg error when resolve IP"
date: 2009-09-22
forum: Installation &amp; Upgrades
---

### Post by Anthrax on 2009-09-22
Hi, please can someone help I have been struggling for days to try and get sarg to give me resolved IP's in my reports but every time I run a report I get the below error. Please can someone give me some insight into this problem.

```
sarg -n /var/log/squid/access.log
SARG: getword loop detected.
SARG: searching for 'x20'
SARG: Maybe you have a broken record of garbage in your access.log file
```

---

### Post by LCRC on 2009-09-26
Same problem here, although I have the problem when using dansguardian access logs.  My squid logs work fine.

```
SARG: sarg version: 2.2.5 Mar-03-2008
SARG: Maximum file descriptor: cur=1024 max=1024, changed to cur=20000 max=20000
SARG: Loading User table: /etc/squid/sarg.usertab
SARG: Reading access log file: access.log
SARG: (util) tbuf=2009Sep26
SARG: (util) period=2009Sep26-
SARG:    Records read: 6799, written: 6799, excluded: 0
SARG: Squid log format
SARG: (util) data=09/26/2009
SARG: (util) tbuf=2009Sep26
SARG: (util) period=2009Sep26-2009Sep26
SARG: Period: 2009Sep26-2009Sep26
SARG: pre-sorting files
SARG: (util) dirname=/var/www/squid-reports/2009/09/26
SARG: (util) wdir=/var/www/squid-reports/2009Sep26-2009Sep26
SARG: Making period file
SARG: Making file: /tmp/sarg/robert-********-macbook-pro.local
SARG: Making file: /tmp/sarg/caroline-********-macbook-pro.local
SARG: Making file: /tmp/sarg/mystic.logicalchaos.inc
SARG: Making file: /tmp/sarg/iRob.logicalchaos.inc
SARG: Making file: /tmp/sarg/guest.logicalchaos.inc
SARG: Making file: /tmp/sarg/gnome.logicalchaos.inc
SARG: Sorting file: /tmp/sarg/robert-********-macbook-pro.local
SARG: Sorting file: /tmp/sarg/caroline-********-macbook-pro.local
SARG: Sorting file: /tmp/sarg/mystic.logicalchaos.inc
SARG: Sorting file: /tmp/sarg/iRob.logicalchaos.inc
SARG: Sorting file: /tmp/sarg/guest.logicalchaos.inc
SARG: Sorting file: /tmp/sarg/gnome.logicalchaos.inc
SARG: Reading DansGuardian log file: /var/log/dansguardian/access.log
SARG: Sorting file: /tmp/sarg/dansguardian.log
SARG: getword loop detected.
SARG: searching for 'x20'
SARG: Maybe you have a broken record or garbage in your access.log file.

```

---

