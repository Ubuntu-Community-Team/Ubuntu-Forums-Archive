---
title: "Still problems with courier-imap"
date: 2008-07-19
forum: General Help
---

### Post by gurkburk on 2008-07-19
Ive been struggling for a while now and just feels like its going backwards.
Im trying to install courier on my server, so that I can connect t it and read mails using IMAP.
I also wanto use the Maildir format, to store mails.

Now, after installing and uninstalling, configuring and swearing ive just ended up with nothing, now I cant even connect to the bloody thing.

Right now, when trying with outlook explorer, I get an error that the server cant even be reached.

Doing a "ps -aux | grep courier" I get 2 rows(I removed the row about the ps-aux command):

> root      7628  0.0  0.0   1904   452 ?        S    15:33   0:00 /usr/sbin/courierlogger -pid=/var/run/courier/imapd.pid -start -name=imapd /usr/sbin/couriertcpd -address=0 -maxprocs=40 -maxperip=20 -nodnslookup -noidentlookup 143 /usr/lib/courier/courier/imaplogin /usr/bin/imapd Maildir
root      7629  0.0  0.0   2008   616 ?        S    15:33   0:00 /usr/sbin/couriertcpd -address=0 -maxprocs=40 -maxperip=20 -nodnslookup -noidentlookup 143 /usr/lib/courier/courier/imaplogin /usr/bin/imapd Maildir

So as faar as I can tell the bloody thing is atleast running.

I have found so many guides about courier but they all include connecting it to mysql, spamassassin, claAV and whatever, first I just want the thing to work!! (although I ofcourse realise all the extra programs add alot of almost required function, its just overkill for me at this point).

Sidenote: I have mails in /home/user/Maildir/new
I have getmail4 on the server, and by running it manually (for testing) it fetches mails, and delivers them to the Maildir directory.

Please help :(

---

