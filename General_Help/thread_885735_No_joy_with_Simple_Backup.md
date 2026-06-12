---
title: "No joy with Simple Backup"
date: 2008-08-10
forum: General Help
---

### Post by Roger D on 2008-08-10
Hi

Has anyone been able to get Simple Backup to work?

All of my working files are in a directory named '1'. At the moment my basic backup strategy involves periodically coping this directory onto an external hard disk - it's crude, time-consuming, but at least I know it works.

I've been trying to do something similar with Simple Backup - should be simple, and, being incremental should be a bit faster.

I start it up, select, 'Use custom backup setting', click on the 'include' tab, highlight '/home/, click the '+ Add Directory' button, highlight my '1' directory, click the 'open' button, so that /home/roger/1 now appears on the 'include' tab page. I click on /home/roger/1 to highlight it, then click on the 'Backup Now!. I get a message about a process being started in the background, and, sure enough, a folder with a very long name appears in /var/backup.

However, when I start Simple Backup Restore, I get the message:

"Error: no backups found in the target directory".

For a program that supposed to be simple, Simple Backup seems extraordinarily hard to get to work.

Anybody any bright ideas?

Roger D

---

### Post by alpha-buntu on 2010-05-03
worked for some time. now it doesnt. I somehow dont trust this tool

---

### Post by Zill on 2010-05-03
Roger D:  Your backup archive should be in /var/backup by default although you can change this if you wish.  Assuming that your backup can be seen their, either via Nautilus or the terminal, then you need to ensure that Simple Backup Restore also points to this location, using either the default or a custom path.

Then select the appropriate backup archive file from the pull-down list of available backups.  This should then show the files and folders available to restore.

Note that, by default, your *entire* /home directory (including all sub-directories) is included, so it is unneccessary for you to specify a sub-directory ("1") within it.  The default includes/excludes are, imho, quite sane and so I suggest that you may like to try the default settings for SBackup and then fine-tune it once it is working correctly.  You can quickly test the defaults by renaming the current config file and then restarting SBackup Config and creating a new backup archive:

```
sudo mv /etc/sbackup.conf /etc/sbackup.conf_original
```

---

