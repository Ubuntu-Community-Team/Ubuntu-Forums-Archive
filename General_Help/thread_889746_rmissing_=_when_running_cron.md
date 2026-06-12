---
title: "rmissing = when running cron"
date: 2008-08-14
forum: General Help
---

### Post by stikboy63 on 2008-08-14
Hi all, I am having a weird issue with one of my crons I am trying to run.

Running Ubuntu 7.10 Server

crontab entry:
00 00 * * * /home/user/bin/perl/script.pl -conf=/home/user/bin/perl/myconf

ps -ef:
user   14060 14059 94 00:53 ?        00:13:49 /usr/bin/perl -s /home/user/bin/perl/script.pl -conf /home/user/bin/perl/myconf

notice that when the proc runs, it removes the = after -conf, causing my script not to read and thus not running properly.

I have tried crontab and fcrontab, edited /etc/fcron.conf and changed shell from /bin/sh to /bin/ksh and /bin/bash, all with the same results.

I have created a test.sh containing
/home/user/bin/perl/script.pl -conf=/home/user/bin/perl/myconf

and tried calling test.sh from crontab as other crons that don't use the -conf= work, but this gave the above results too.

this happens under a users cron and under root cron.

double quotes, single quotes, (=), == have been tried with varying results, but still not running successfully.

Has anyone seen an issue like this or have any idea what I can try next?

Thanks,

Scott

---

