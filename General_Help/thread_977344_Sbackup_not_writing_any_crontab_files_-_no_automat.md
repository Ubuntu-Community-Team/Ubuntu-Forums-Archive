---
title: "Sbackup not writing any crontab files - no automatic backups"
date: 2008-11-10
forum: General Help
---

### Post by jwood1961 on 2008-11-10
I just did a clean install of Intrepid (8.10) fully updated, but find I still have the problem I had under Hardy. I set sbackup to custom settings, with run every day at precisely 3am, full backup once every 7 days. However, no jobs ever run; I can only get a backup by doing it manually. Crontab shows no crontab jobs for any user, and indeed there are no files in the relevant /var/spool/cron directories. This looks like a bug, but I don't see any other posts reporting this.

The 'simply' option does not seem to work either although there is an sbackup file in /etc/cron.d, it points to /usr/sbin/sbackupd which has code in it. So I don't know why that won't work.

Everything about the sbackup setup is as installed from the install image, apart from then using the sbackup-conf screen. Anybody else see this, or have any ideas of what I may be doing wrong?

JW

---

### Post by stevepowell99 on 2009-04-10
yep, I have exactly the same problem. sbackup runs when I press the manual button in the config wizard, but it never runs otherwise whatever setting I have. It might be writing or trying to write some cron file somewhere, but I can't tell where.
I can run sbackupd from a root cron job, but I don't think I will then have the advantage of the logarithmic "keep" strategy.

---

### Post by stevepowell99 on 2009-04-10
actually, I think the logarithmic purge option will work because it is set in /etc/sbackup.conf. 
so your workaround would be just to do e.g.
sudo crontab -e -u root
and set e.g. 
```
/50 * * *  * /usr/sbin/sbackupd 
```
there.
I'd still like to know why it doesn't work automatically though.

---

### Post by NimoTh on 2009-05-24
In that code of yours, can you tell me where I specify the time when sbackup will be executed? I'm a newbie to cron.

TIA
Martin

---

