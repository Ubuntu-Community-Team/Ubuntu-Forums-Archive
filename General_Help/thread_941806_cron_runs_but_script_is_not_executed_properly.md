---
title: "cron runs but script is not executed properly"
date: 2008-10-08
forum: General Help
---

### Post by ichbindev on 2008-10-08
I have the following bash script for daily backing up of mysql database and deleting some temporary files. Its main steps are: (1) Use mysqldump to create a backup .sql file; (2) Zip up the file; (3) Copy the file to a Windows shared folder using smbclient; (4) Delete the sql and zip file created; (5) Delete some files from a directory.

#!/usr/bin/env bash
Date=`date "+%Y%m%d%H%M%S%n"`
DBUser="mydbuser"
UserPassword="mydbpassword"
BkpUser="mybkpuser"
BkpPassword="mybkppassword"
mysqldump mydatabase -u$DBUser -p$UserPassword > /home/me/daily-backup/mydatabase.sql
cd /home/me/daily-backup/
zip mydatabase-"$Date".zip mydatabase.sql
smbclient "//bkpserver/backup" -I10.10.1.10 -Wworkgroup -U $BkpUser%$BkpPassword < /home/me/scripts/smbclient-commands
rm mydatabase.sql mydatabase-"$Date".zip
cd /home/me/tempfiles/
rm -f *.csv

The file smbclient-commands has the following contents
prompt
mput *.zip
quit

I set up cron with the following

crontab -u me -e

and then input the following line

00 05 * * * /home/me/scripts/dailybackup.sh

cron runs successfully, but instead of executing the shell script properly, it creates a binary file in /home/me/daily-backup/. When I run the script manually, it works perfectly. I have given execute permissions on script to user and other, read is allowed for user, group, and other. daily-backup directory has read, write, and execute permission for user and other. smbclient-commands file has read permission for user, group, and other; write permission to user.

I am using Ubuntu Gutsy server edition. Is there something I am doing wrong and need to correct so that it runs properly?

---

### Post by Titan8990 on 2008-10-08
I can't say for sure what you problem is but I can help to clean that script up a little.

"cd /home/me/daily-backup/"

This is bad practice for scripts. You should **always** use absolute paths. So that would change the next line to:

zip mydatabase-"$Date".zip /home/me/daily-backup/mydatabase.sql


So, it is correctly creating the mysqldump but failing at zipping and/or transfering it via SMB?

---

### Post by ichbindev on 2008-10-08
It's creating the dump and the zip files but not able to copy the file via smbclient. Instead, there is a binary file created with weird names like ziqaxKgX or something like that.

---

### Post by ichbindev on 2008-10-08
i found a tutorial online ([http://www.techsneeze.com/smbclient-to-backup-files-from-linux-to-a-windows-server](http://www.techsneeze.com/smbclient-to-backup-files-from-linux-to-a-windows-server)) which shows how to use the -c flag and give commands while calling smbclient. i will try that solution instead of getting commands from a file and see if that works. will post once i have results.

---

### Post by ichbindev on 2008-10-16
i found out that getting mysql dump and then zipping it is not the problem. when it zips the directories, then it creates a binary file with a weird name and also doesn't move anything via smbclient. if i comment out the lines where it zips up directories, then the scheduled job is able to move the zip of mysql dump.

---

### Post by ichbindev on 2008-10-23
i could not find a solution but someone else did. i found a blog post ([Problem running bash script in cron]("http://codeghar.wordpress.com/2008/10/19/problem-running-bash-script-in-cron/")) referencing my own question here, and a solution was posted there. i followed the instructions and got the problem solved.

---

