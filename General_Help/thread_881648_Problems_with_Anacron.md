---
title: "Problems with Anacron"
date: 2008-08-06
forum: General Help
---

### Post by birdm110167 on 2008-08-06
Hi there

I have a small issue and wondering if anyone could point me in the right direction please.


I am a fairly seasoned DOS user of some 20 odd years and relatively new to Ubuntu.  Please excuse me if I use the wrong terminology.

I have three “batch” files which essentially (1)take a copy of a Subversion directory and put them in a temp folder.  This folder is then (2)tape archived with tar and lastly (3)45ftp’d over to a Backup server.

My problem is this:

If I double click each batch file and when prompted to click “Run in Terminal” the batch files all work correctly, resulting in folders and tar files s of 177.2 MB  big.

However If I schedule the batch files to run late at night with anacron then the batch files still run however the resulting folders are only 119.9MB larger – quite a difference in size.

A similar issue with another set of batch files give me the following sizes – Manually run give me 1.9GB folder in 17 files, whereas a Scheduled run gives 44.7MB in 4 files – SO EVEN FILES ARE NOT BEING COPIED . 

What am I missing.  The batch files are scheduled to run 20 minutes between them, more than enough time for each job to complete.

Below is the contents of the first batch files which creates the folder that then gets zipped and ftp’d over.





#!/bin/bash
#
echo "Creating Quality Repository backup";
mkdir /home/software/repos_backup/Quality;
sudo svnadmin dump /var/project_data/repos/Quality/Quality > /home/software/repos_backup/Quality/Quality;

If you would like more details please just ask.

---

### Post by Yannick Le Saint kyncani on 2008-08-06
sudo can't ask a password if runned from cron, so you do put your task in root's crontab, right ?

---

### Post by birdm110167 on 2008-08-06
Hi there, thanks for the reply.

The statement that kicks the batch file off is in the anacron config file and is below.

40 23   * * *  root sudo /home/software/repos_backup/create_quality_backup

Does this help?

---

### Post by Yannick Le Saint kyncani on 2008-08-06
> **birdm110167 said:**
> 40 23   * * *  root sudo /home/software/repos_backup/create_quality_backup

Well, that's not the way I would do it.

I would setup a root crontab :

- sudo -i
- crontab -e
- use this line : "40 23 * * * /home/software/repos_backup/create_quality_backup"

---

### Post by birdm110167 on 2008-08-06
Hi there

This has now been solved.  (just before I saw your reply Yannick Le Saint kyncani, many thanks for your suggestion - I will look at this also to see if that is a cleaner method. ;o))

After reading this article [https://help.ubuntu.com/community/CronHowTo](https://help.ubuntu.com/community/CronHowTo)
I used this command :

sudo crontab -e

and put my batch file calling statements in there.  Maybe not wise but it works.

Then I removed all "sudo"s from my batch files and Voila it works.

Many thanks to the help I got.

;o)

---

