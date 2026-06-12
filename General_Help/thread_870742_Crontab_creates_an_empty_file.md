---
title: "Crontab creates an empty file"
date: 2008-07-26
forum: General Help
---

### Post by PaulusEm on 2008-07-26
First at I want to tell that I'm from the Netherlands, so I'm sorry if I'm hard to understand :)

I've created some days ago a bash script to make a backup of my openbravo database which is using PostgreSQL.
When I run this SH file it's creating a nice backup located somewhere in my home folder, with a size of 27,3mb.

Now I've created a crontab to make automatically a backup every day, my crontab does look like:
59 23 * * * "/home/paul/Database Backup/backup.sh"

And this is the file:
```
#!/bin/bash
HOMEDIR="/home/paul"
FILENAME="openbravo-`date --date="today" +%d-%m-%Y-%H%M`.backup"

# Does the Main Backup Directory exists?
if [ -d "$HOMEDIR/Database Backup/" ]
    then
        sleep 0
    else
        mkdir "$HOMEDIR/Database Backup/"
fi

# Does the Year Backup Directory exists?
if [ -d "$HOMEDIR/Database Backup/`date --date="today" +%Y/`" ]
    then
        sleep 0
    else
        mkdir "$HOMEDIR/Database Backup/`date --date="today" +%Y/`"
fi

# Does the Month Backup Directory exists?
if [ -d "$HOMEDIR/Database Backup/`date --date="today" +%Y/%m`" ]
    then
        sleep 0
    else
        mkdir "$HOMEDIR/Database Backup/`date --date="today" +%Y/%m`"
fi

pg_dump -i -h 127.0.0.1 -U tad -F c -b -v -f "$HOMEDIR/Database Backup/`date --date="today" +%Y/%m/`$FILENAME" openbravo
```

When I open this file in a terminal it's making a file with the size of 27,3mb, but when the crontab runs this command it only makes the file, 0 bytes so no data..

Wondering why this is happening, I've tried this on Ubuntu 7.10 and 8.04, and also on different servers (32bit and 64bit)..

Hope somebody can help me out, because this is a little frustrating :mad:

Paul :)

---

### Post by mike2357 on 2008-07-26
I suggest changing your cron command to:

59 23 * * * "/home/paul/Database Backup/backup.sh" > OUT_BACKUP 2>&1

This will create an output file so you can see any output or error messages that are being generated.  The "2>&1" means to send error messages to the same file as standard output, which is this case is OUT_BACKUP.  It will be created in your home directory.

cron runs with a limited PATH, so you may end up having to set the PATH in your script.

I don't think I've solved your problem, but hopefully you will be better able to debug whatever is going on.  If you can't tell, post back with anything relevant from OUT_BACKUP and I'll be glad to take another look.

---

### Post by PaulusEm on 2008-07-26
Jul 26 12:46:01 openbravo /usr/sbin/cron[5247]: (paul) RELOAD (crontabs/paul)
Jul 26 12:46:01 openbravo /USR/SBIN/CRON[9510]: (paul) CMD (paul sh "/home/paul/Database Backup/backup.sh" > OUT_BACKUP 2>&1)

Aint creating a file now anymore :P

Edit:
Wait, I had the wrong command, I've removed "paul" and now it's working again ;)
Where is the OUT_BACKUP file located now? Since the backup file is still 0 bytes.. :P

---

### Post by mike2357 on 2008-07-26
OUT_BACKUP should be in Paul's home directory.

---

### Post by PaulusEm on 2008-07-26
Hmm this is weird, when I add "> OUT_BACKUP 2>&1" it's making the backup, but when I remove it the file stays 0 bytes.
Is this because pg_dump cant the processing? (Its saying which tables he is processing ;))

Edit:
I've now added "> output.tmp 2>&1" to the pg_dump command, and it's working fine ;)
Ill add rm "$HOMEDIR/Database Backup/output.tmp" at the bottom so it deletes the file when it's done :)

---

### Post by mike2357 on 2008-07-26
I'm with you -- it certainly is weird.  I have no idea why having an output file makes a difference.

When I use cron to generate a script, I generally make the script a Bourne shell script (with #!/bin/sh at the top) rather than /bin/bash.  That's because when you use /bin/bash, your .bashrc file will be sourced, which may have something that requires terminal input and output.  On the other hand, if you were to switch to the Bourne shell, you could be missing out on settings that are in your .bashrc file, so it could make things worse for you.

It sounds like you've solved your problem and I'm just pontificating, so I'll sign off.

---

### Post by PaulusEm on 2008-07-26
> **mike2357 said:**
> I'm with you -- it certainly is weird.  I have no idea why having an output file makes a difference.

When I use cron to generate a script, I generally make the script a Bourne shell script (with #!/bin/sh at the top) rather than /bin/bash.  That's because when you use /bin/bash, your .bashrc file will be sourced, which may have something that requires terminal input and output.  On the other hand, if you were to switch to the Bourne shell, you could be missing out on settings that are in your .bashrc file, so it could make things worse for you.

It sounds like you've solved your problem and I'm just pontificating, so I'll sign off.Yup, my problem is solved :) Ofcourse with your help! So thanks for that :)

---

