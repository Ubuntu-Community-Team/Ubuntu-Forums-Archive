---
title: "Sbackup Alternatives?"
date: 2008-09-25
forum: General Help
---

### Post by undoIT on 2008-09-25
Sbackup has never been kind to me. It simply doesn't work. Are there any backup alternatives with GUI for doing incremental backups?

---

### Post by Ryadt on 2008-09-25
Try linbaku. Have a look here: [http://code.google.com/p/linbaku/](http://code.google.com/p/linbaku/)

---

### Post by undoIT on 2008-09-25
linbaku looks great. thanks for the recommendation, i'll give it a go.

---

### Post by undoIT on 2008-09-28
Unfortunately, linbaku is far too simple. It only does complete system backups. I need to backup maybe half of what is on my hard drive, so it is a huge waste of time and CPU to do the whole magilla. Also, it doesn't seem to do incremental backups. No scheduling either. Any other GUI backup apps?

---

### Post by undoIT on 2008-10-03
Well, rsync is the way to go imo. It is really simple to use rsync.

Open up terminal. Paste in command. Let it run.

You don't have to create an archive, so the backup files are immediately usable and it won't be hogging the CPU to compress the backup while running. It is also incremental.

I've figured out how to do this for a single folder, with the following command:

For example (backup to external hard drive):

```
rsync -avh ~/Documents /media/disk-1
```

How would I write a script to backup multiple folders?

---

### Post by _sAm_ on 2008-10-03
Agree, rsync is nice and rsync +cron is wonderful! If you want rsync with gui check out Unison.

---

### Post by undoIT on 2008-10-03
I installed Unison about 15 minutes ago. Seems like it only allows one folder at a time.

---

### Post by Zill on 2008-10-03
> **undoIT said:**
> Sbackup has never been kind to me. It simply doesn't work...
Linux has always been about choice and I respect your opinion.

However, I have been successfully running SBackup automatically on our three PCs for years without any problems so I can't agree with your assertion that "It simply doesn't work".

If you post what difficulties you are having then I am sure you *could* get SBackup to work :-)

---

### Post by undoIT on 2008-10-03
I have never been able to create a backup .tgz archive that could be successfully opened. If I try to open it manually, it gives an error message. And, if I try to restore a file / folder from the backup, it creates a temp folder that is owned by root. Not sure if the ownership issue was due to not chowning the external hard drive after formatting.

Anyhow, i'd rather not create an archive, so rsync is working quite well for the time being.

---

### Post by Zill on 2008-10-04
SBackup saves the .tgz archive to a directory owned by root.  I can then manually restore file(s) to the original location or a directory of my choice.  The restored files retain the ownership of the original files.

I save my backups to a drive formatted with reiserfs.  If your external hard drive is formatted with Windows FAT, rather than a linux file system, then this *may* be part of the problem.  AIUI, FAT does not preserve file permissions - but someone else may be able to clarify this ;-)

Still, I am pleased you have got rsync working to your satisfaction :-)

---

### Post by oldefoxx on 2010-02-28
I don't know the problem with SBackup.  The Synaptic Package Manager had no problem installing it to 9.04, and I found the Simple Backup Config and used it, but after configuring it and saving the configuration, I would press Backup Now, and it would return a process ID, but nothing else happened.  Checking on the Processes running with ps did not show it running.  No information provided on what I should have observed, how long it might take, or anything else.  Any ideas?

---

### Post by Zill on 2010-03-01
oldefoxx:  This is a rather old thread you have resurrected!

It sounds to me like SBackup is running as designed - no feedback is given after the process starts as it is *supposed* to run in the background.

You should find your backup archive in your specified destination directory, which by default is /var/backup but can, of course, be changed to any other location on your file system.

SBackup does take considerable time to create and save the archive, obviously depending on the amount of source data and the speed of your PC hardware etc.  If you monitor the destination directory you will see the file size gradually increasing as the process continues.  For example, my systems can take around 15 minutes to backup approx 5GB of data.

See [https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite]("https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite") for further details.

---

