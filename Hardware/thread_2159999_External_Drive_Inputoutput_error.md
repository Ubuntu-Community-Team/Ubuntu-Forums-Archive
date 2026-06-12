---
title: "External Drive Input/output error"
date: 2013-07-05
forum: Hardware
---

### Post by Saviosilva on 2013-07-05
Hi there
I have an external drive that I plug to a server to do its back up
Everytime the drive is plug to the server I get an error message cannot mount drive to location /mount/user/BackupDrive input/output error
If I plug the external drive on my windows pc works fine
The drive is formatted ntfs.
If I mount the drive to a differt location /mnt/user/BackupDrive 
The drive will mount fine but when I run the cp command to copy the data I get the cp cannot copy the data input/output error
Can anyone help out please

Thanks

---

### Post by TheFu on 2013-07-05
NTFS is not really a Linux compatible file system. Sure, it works most of the time, but important file metadata is lost when placing Linux files onto NTFS partitions.  User, group, ACLs and normal permissions are all lost.  Also, special files cannot be copied over  FIFOs, PIPEs, devices .... File security on NTFS is basically zero too.  Those things might not matter at all.

Is the /etc/fstab  modified to use UUID references for this specific HDD? Especially for portable drives, using a UUID is a big help. The line must include the NTFS parameter.
The directory that holds the mount needs to be owned by the correct user - probably the user doing the backup.  During the mount, it might be necessary to ensure that same user is part of the mount options.

Using **cp** to perform backups can work fine for 100% data files, though there are better, more efficient tools, like rsync, if you just need a single mirrored copy.  For real backup processing, following a few best practices [http://blog.jdpfu.com/2011/11/12/best-practices-for-home-desktop-computer-backups](http://blog.jdpfu.com/2011/11/12/best-practices-for-home-desktop-computer-backups) makes sense. If you must use NTFS and want to retain most of the common file permissions, something like **tar** or **rdiff-backup** can address that concern. File metadata is stored regardless of the target file system type.

If you can provide more specifics about exactly how you are performing each step in your process, someone should be able to help. Definitely list the specific tools used and any log file messages [http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files](http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files) too, since sometimes there are kernel errors in log files that CLI programs don't show.

A few other thoughts ...  Linux can often see when drives are failing before Windows does, so I'd validate that the HDD and USB interface are all working.  USB cables and well-used plugs on PCs fail all the time. Try a different USB port first, if that doesn't help, swap the cable.

Good luck!

---

### Post by ajgreeny on 2013-07-05
Do you always unplug the disk properly from Windows, ie do you go through the "Remove safely" procedure?

If you simply unplug the drive from windows it will not normally be possible to mount it in Linux as it will still be flagged as "in use".  Try plugging it back in Windows and removing properly then try in ubuntu again.

---

### Post by Saviosilva on 2013-07-08
Hi there

Sorry for the Delay replying...it has been a nice weekend over UK :)

The process is:
1- i plug the drive in my windows laptop and format using windows tools to ntfs( i use default block size)
2- I use windows tool to remove drive safely
3- plug the drive to the server
4- the i get an error saying : [COLOR=#000000]cannot mount drive to location /media/user/BackupDrive input/output error
[/COLOR]5- i created a BackupDrive directory at a different location thinking the /media/user path was the cause of the issue -> new path /mnt/user/BackupDrive
6- i run the command fdisk -l  and i can see the /dev/sdd1/ there
7- i run a command as a root mount /dev/ssd1 /mnt/user/BackupDrive
8- i run a command df and i can see the mounted drive there
9- i navigate to the /mnt/user/BackupDrive and i can create new directory via mkdir command
10- when i run my script to make a backup i get a error : cp command to copy the data I get the cp cannot copy the data input/output error

After i get this error message, i can no longer write to the drive(no even create a new directory (mkdir)) however i can delete any files that are there via the rm -r commanad

This is really weird. Hopefully you will be able to guide me to the correct path

Please let me know if furhter infomation is required

PS. the script is just a cp command and it worked for 1 month ar so but i am now getting this error for some reason

#!/bin/bash
echo "===================================================================================="
echo "Starting Backup"
echo "===================================================================================="
START=$(date +%D)
FOLDER_NAME1=`echo $START | tr -s '/' | tr '/' '_'`
FOLDER_PATH1='/mnt/home/BackupDrive'
BACKUP_PATH1=$FOLDER_PATH1/flb_$FOLDER_NAME1
mkdir -p '$BACKUP_PATH1'
cp -r /mnt/home/7f49efb0 $BACKUP_PATH1
echo " Done!

---

