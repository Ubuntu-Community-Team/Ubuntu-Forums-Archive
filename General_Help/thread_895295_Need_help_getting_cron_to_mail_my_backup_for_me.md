---
title: "Need help getting cron to mail my backup for me"
date: 2008-08-20
forum: General Help
---

### Post by LeGollemux on 2008-08-20
I backup my mysql databases with backup-manager. it works very well and I always have 5 days of backups stored in the /var/archives directory. These files arent very big. So I would like to mail them to an offsite mailbox (gmail) on a daily basis. This way, should my office be hit by and asteroid my backups should be fine seeing as they are stored on another continent. 

I need a cron script, stored in the relevant cron directory that will mail automatically mail the file.

any ideas?

---

### Post by HalPomeranz on 2008-08-20
Here's a simple cron entry that should do the trick:

```

1 0 * * * mailx -s 'Nightly DB Backup' someuser@example.com <`ls -t /var/archives/* | head -1`

```

Explanation:

-- The first part, "1 0 * * *", tells the cron job to run at one minute after midnight every day.  You may want to change this time to coincide with the time your backup normally finishes ("30 4 * * *" would run the job at 04:30 every morning, etc).

-- "mailx -s 'Nightly DB Backup' [email]someuser@example.com[/email]" means send an email to "someuser@example.com" (change this to be the email address where you want the backups to actually go) with a subject line of 'Nightly DB Backup'.  Note that you may have to install the mailx command from the repos ("sudo apt-get install mailx").

-- The last part uses input redirection ("<") to make the body of the email message contain the appropriate file from /var/archives.  "ls -t /var/archives/* | head -1" returns the pathname to the most recently updated file in this directory (i.e., the most recent backup).

---

### Post by HermanAB on 2008-08-20
You could simply plonk a script into /etc/cron.daily and it will run just after 4am each morning.

Cheers,

Herman

---

