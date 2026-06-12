---
title: "Ubuntu 9.04 - MySQL backup hour problem"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by ddk1965 on 2009-04-27
Upgrade Ubuntu 8.1 -> 9.04 with MySQL server installed.

In the backup script we can't go from 0->24 hour for the start of the backup only from 0->13

A workaround is go to into the crontab line of mabackup and manual change the hour above 13.

Any idea how to solve this problem?

Tx,

Danny
Belgium

ps: I tried also a clean install of 9.04 same problem!

---

### Post by australisblue on 2009-06-23
This isn't going to help much, but I too have run into this problem. The hour seems to go from 0-13 and the minutes from 0-49, which is a slightly strange bug..! So you're not the only one ;-)

---

