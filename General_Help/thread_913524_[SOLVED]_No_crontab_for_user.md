---
title: "[SOLVED] No crontab for user"
date: 2008-09-07
forum: General Help
---

### Post by JockVSJock on 2008-09-07
I created a cronjob that will backup my home directory to an external drive on a daily basis. 

However I have used crontab to create the cron job and want to test it to make sure it works. 

When I run 

```


cmmiller@ladytron:~/backup$ crontab -l
no crontab for cmmiller


```

Checking the directory where crontab calls home: 

```
 
cmmiller@ladytron:~/backup$ ls -l /var/spool/cron
total 12
drwxrwx--T 2 daemon daemon  4096 2007-04-15 06:55 atjobs
drwxrwx--T 2 daemon daemon  4096 2007-02-20 07:41 atspool
drwx-wx--T 2 root   crontab 4096 2006-12-20 08:46 crontabs

```

Do I have to change the permission from root to me?  

Is there a way I can setup a separate crontabs for my user?

---

### Post by HalPomeranz on 2008-09-08
First thing is that the actual crontab entries are stored in files in /var/spool/cron/crontabs.  If a user has cron jobs configured, you'll see a file in this directory named for that user (e.g. /var/spool/cron/crontabs/cmmiller in your case).  

However, since "crontab -l" isn't showing anything, I suspect that whatever procedure you used to create the cron entries for your user ID was incorrect.  Can you explain exactly how you tried to set up the cron entry?

---

### Post by JockVSJock on 2008-09-09
I have a script under my home directory that backs up my home dir on a daily basis. 

```


#!/bin/bash
#backup data on a daily basis via cron job

echo backup started `date` >>~/backup/backuplog
cp * -ar /home/cmiller/ /media/Linux_ext3
echo backup completed `date`>>~/backup/backuplog


```

Then I typed 

```

nano backup_script.cron

```

Which then I typed 

```

0 3 * * * /home/cmmiller/backup/backup_script

```

Then I pressed control + x 

Which backs me out of nano and then I run 

```


cmmiller@ladytron:~/backup$ crontab -l
no crontab for cmmiller


```

EDIT: 

I think I may just have gotten it to work...

[http://crunchbang.org/archives/2007/10/26/howto-setup-a-crontab-file/](http://crunchbang.org/archives/2007/10/26/howto-setup-a-crontab-file/)

I did the following: 

```

cmmiller@ladytron:~/backup$ crontab -u cmmiller ~/backup/backup_script.cron
cmmiller@ladytron:~/backup$ crontabl -l
bash: crontabl: command not found
cmmiller@ladytron:~/backup$ crontab -l
0 3 * * * /home/cmmiller/backup/backup_script

```

---

### Post by Rocket2DMn on 2008-09-09
That looks right to me.  Generally to setup a crontab job, you do
```
crontab -e
```
Save and close.
Then you set up the row as you have above
```
0 3 * * * /home/cmmiller/backup/backup_script
```
Of course, that script must exist and be executable and correctly written.

---

### Post by JockVSJock on 2008-09-10
My cron job ran ok. 

```


cmmiller@ladytron:~/backup$ cat backuplog
backup started Tue Sep 9 20:35:04 CDT 2008
backup completed Tue Sep 9 20:35:09 CDT 2008
backup started Tue Sep 9 20:35:45 CDT 2008
backup completed Tue Sep 9 21:17:59 CDT 2008
backup started Wed Sep 10 03:00:01 CDT 2008
backup completed Wed Sep 10 03:37:50 CDT 2008



```

thanks

---

