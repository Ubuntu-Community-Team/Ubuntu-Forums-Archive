---
title: "Crontab Issue..."
date: 2008-07-26
forum: General Help
---

### Post by Barriehie on 2008-07-26
I've tried to automate my backup and it's working but only as far as the backup file being generated is only 20 bytes...  What's up with this???  Here's my /etc/crontab

```

SHELL=/bin/sh PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin:/home/barrie/myscripts/bash #BackUp the system
00 06 * * Fri root sh /backmeup.sh

```and here's my /backmeup.sh script
```

tar cvpzf /home/barrie/disk/backup-files/bup$(date +%m%d%y).tgz --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/sys --exclude=/home/barrie/disk --exclude=/var/spool/havp /

``` TIA, Barrie

---

