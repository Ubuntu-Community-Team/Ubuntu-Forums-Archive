---
title: "Handy backup script..."
date: 2008-10-25
forum: General Help
---

### Post by ragtag on 2008-10-25
Hi,

 I'm just posting this for anyone that might want it. It's a script I use for backing up my Ubuntu home folder (it should work most variants of Linux). It's pretty simple and easy to use. I'll explain below.

```
#!/bin/sh
# Quick backup hack by Ragnar Brynjulfsson
# License: Public domain (i.e. do what you like with it).
# - Please note that there is very little error checking here, so use at your own risk.
# - The script makes incremental copies in seperate folders, marking them with the current time and date.
# - Only the files that have changed are stored each time, the rest are hard linked to earlier copies.
# - You can delete folders containig older versions at any time to save disk space, just leave the latest one if you don't want to loose your backup.

# Change backupsource to point to the folder you want to backup.
backupsource="/home/your_username"
# Change backupdestination to where you want to store your backup.
backupdestination="/media/disk/your_backup"
# Text file containing files and folders to exclude from the backup.
exclude="/home/your_username/exclude.txt"

date=`date +%F_%R.%S`
if [ -d $backupdestination ]
    then
    echo "Starting backup of $backupsource to $backupdestination/$date"
else
    echo -n "The backup destination $backupdestination does not exist, do you want to create it (y/n)?"
    read yesno
    if [ $yesno = "y" ]
    then
	mkdir -p "$backupdestination"
    else 
	echo "Destination folder $backupdestination does not exist, and was not created. Exiting."
	exit 0
    fi
fi
# Ugly hack to find the latest version, assumes folder is empty or contains backups by this script.
for i in $backupdestination/*
  do
  version="$i"
done
# Run the actual rsync that makes the backup.
if [ "$backupdestination/*" = "$version" ]
then
    echo "No previous version found, creating initial backup..."
    echo "rsync -av --delete --delete-excluded --exclude-from=\"$exclude\" \"$backupsource/\" \"$backupdestination/$date\""
    rsync -av --delete --delete-excluded --exclude-from="$exclude" "$backupsource/" "$backupdestination/$date"
    echo " "
    echo "Initial copy complete ($backupdestination/$date)."
else
    echo "Creating incremental backup..."
    echo "rsync -av --delete --delete-excluded --exclude-from=\"$exclude\" --link-dest=\"$version\" \"$backupsource/\" \"$backupdestination/$date\""
    rsync -av --delete --delete-excluded --exclude-from="$exclude" --link-dest="$version" "$backupsource/" "$backupdestination/$date"
    echo " "
    echo "Incremental copy complete ($backupdestination/$date)."
fi

exit 0

```

You need to change three lines in this script to make it work for you, these are backupsource, backupdestination and exclude. The script uses rsync and hardlinks. Basically it creates an original complete copy of your files at your backupdestination. The next time you make a backup, it uses your previous backup as reference and only copies over files that have changed, the rest are hard linked to the previous version. This means that each new version looks like a complete copy of all your files, and is easy to browse to should you want to restore anything. Hardlinks are multiple files that point to the same data on the drive, the data itself is not deleted till all files pointing to it are deleted. If you change one of them though, all will be changed, so it's a good idea not to change the files in your backup. :)

The exclude file can look something like this. This would exclude all hidden files in /home/your_username as well as incoming, temp and windows. See 'man rsync' for details.

```

/.*
/incoming
/temp
/windows

```

Note that the script is a bit stupid, so don't put other stuff besides your backups created by the script in your backupdestination folder. If you create multiple instances of the script to backup different paths, create a backupdestination for each.

I currently use it to backup around 150gig to an external drive without problems.

Hope someone finds this useful. 

 Ragnar

p.s. If you have some clever improvements to this or find bugs:confused:, feel free to let me know.

p.p.s. I use evolution calendar reminder to remember to connect the external driva and actually run the backup script.

---

### Post by koenn on 2008-10-25
rather reminds me of this : 
[http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/)

---

