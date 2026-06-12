---
title: "Script failing as cron job"
date: 2008-09-09
forum: General Help
---

### Post by The Tronyx on 2008-09-09
Hello,

I wrote a script called archive.sh and when I add it to crontab, it fails but it will work successfully if run manually.

The contents of my crontab are:
```

# m h  dom mon dow   command
#0 1 * * * /usr/sbin/oinkmaster -o /etc/snort/rules/
0 1 * * * /root/bin/archive.sh
*/1 * * * * perl /usr/share/pmgraph-0.2/pmgraph.pl /usr/share/acidbase/perfmon/ /var/log/snort/snort.stats >> /var/log/perfmon.log

```
I have tried appending sh root to the beginning of the second line so that it reads, "0 1 * * * sh root /root/bin/archive.sh" but that has not succeeded.

The script itself (archive.sh) contains the following:
```

#!/bin/bash
#kill -9 `pidof snort`
#kill -9 `pidof barnyard`
/usr/bin/mysqldump snort > /snortbackups/snort`date +%F`.sql
/usr/bin/mysql snort_archive < /snortbackups/snort`date +%F`.sql
/usr/bin/mysql snort < /root/bin/mysql.sh
/usr/bin/wget http://www.emergingthreats.net/rules/emerging-drop-BLOCK.rules -O /etc/snort/rules/emerging-drop-BLOCK.rules
/usr/bin/wget http://www.emergingthreats.net/rules/emerging-compromised-BLOCK.rules -O /etc/snort/rules/emerging-compromised-BLOCK.rules
/usr/bin/wget http://www.emergingthreats.net/rules/emerging-botcc-BLOCK.rules -O /etc/snort/rules/emerging-botcc-BLOCK.rules
/usr/bin/wget http://www.emergingthreats.net/rules/emerging-rbn-BLOCK.rules -O /etc/snort/rules/emerging-rbn-BLOCK.rules
/usr/bin/wget http://www.emergingthreats.net/rules/emerging-dshield-BLOCK.rules -O /etc/snort/rules/emerging-dshield-BLOCK.rules
/usr/bin/perl /usr/src/oinkmaster-2.0/contrib/create-sidmap.pl /etc/snort/rules > /etc/snort/sid-msg.map
/usr/sbin/restartsnort

```
Any help is greatly appreciated.  Thanks!

---

### Post by cdtech on 2008-09-09
Be sure you have the proper permissions set and if your running it as root use "sudo su" and then "crontab -e" to edit root's cron jobs.

---

### Post by The Tronyx on 2008-09-09
> **cdtech said:**
> Be sure you have the proper permissions set and if your running it as root use "sudo su" and then "crontab -e" to edit root's cron jobs.

Hello,

The permissions on the file are correct and crontab is being edited with the proper user privileges.

Thanks

---

### Post by cdtech on 2008-09-09
You have a "bin" directory under your "/root" directory?

Shouldn't that be "/bin" instead?

---

### Post by jigsaws on 2008-09-09
What does it mean "fails"? Run but fail or not run? Anything in logs/mail from cron?

---

### Post by The Tronyx on 2008-09-09
It doesn't do anything and there is nothing in the logs.

---

### Post by bingoUV on 2008-09-09
1. To troubleshoot, redirect the output/error of the script in crontab to some file so that you know what happened. Cron is also supposed to send a mail, but you might have missed it.
```

0 1 * * * /root/bin/archive.sh 2>&1  >> /tmp/cronlog

```

2. **crontab is being edited with the proper user privileges**
It is not about proper user privilege. One is root's crontab. Another is normal user's crontab. Root user's crontab needs to be edited as root. Normal user's crontab is to be edited as that user. Both are proper user privileges but they edit different crontabs. Since you want to edit the crontab of root, make sure that you do the following, or equivalent.
```

sudo -i
crontab -e
exit

```

---

