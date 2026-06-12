---
title: "Rsync script fails in cron job"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by metzler on 2009-08-13
Need help setting up cron job to sync two local drives using webmin...  if I execute the rsync command from the command shell it works fine... running it from a script in a cron job fails.  This is a very straight forward script, so I hope someone can point me in the right direction.

here's the error when the cron job runs:   [COLOR=Blue]/bin/sh: /root/rsync.sh: not found[/COLOR]


1.  here's the script rsync.sh:

[COLOR=Blue]#!/usr/bash
rsync -av --rsync-path=/usr/bin/rsync /mnt/public/files/ /mnt/backup/[/COLOR]

2.  Cron job to run rsync.sh:

> crontab -l
46 14 * * * /etc/webmin/cron/tempdelete.pl
0 3 * * 0 /etc/webmin/fsdump/backup.pl 171241248421337
0 3 * 1,4,7,10 1 /etc/webmin/fsdump/backup.pl 156931248632130
0 20 1,20 * * /etc/webmin/backup-config/backup.pl 124659720815629
[COLOR=Blue]0,30 * * * * /root/rsync.sh[/COLOR]

---

