---
title: "[SOLVED] Tungsten E hotSync with gnome pilot"
date: 2008-11-28
forum: General Help
---

### Post by dragos240 on 2008-11-28
Help, i'm trying to hotsync my palm pilot tungsten E with my ubuntu intreped ibex and gnome-pilot, it's not sync-ing. Can anyone give me a guide or something, and tell me if the origonal tungsten E works with gnome-pilot.

---

### Post by dragos240 on 2008-11-28
Bump. Sorry for double posting... but it's on the third page and i really need help

---

### Post by dragos240 on 2008-11-28
Bump (again)

---

### Post by dragos240 on 2008-11-29
Hey! Four bumps in a row, what is with this. I need some help!

---

### Post by dragos240 on 2008-11-29
I'm officially done with this, *sigh* i'm really gonna need eaither another section or another forum. Otherwise this isn't really worth septi-posting. Topic resolved (not really)

---

### Post by dentonlt on 2008-12-04
Sorry you didn't find the answer you wanted, (!). I normally don't show up here, but have had similar problems with gnome-pilot.

You probably know that gnome-pilot is just a wrapper for pilot-xfer and some other command-line tools. Since I had the same problem as you, I put together two scripts for syncing - one to back up, one to restore. Functional, not pretty.

I don't believe gnome-pilot is set up as a daemon to 'listen' for the palm sync/attachment. You have to invoke gnome-pilot first. I had luck by opening the gnome-pilot settings window, then pressing hotsync on the palm. Otherwise, the hotsync wouldn't get recognized. I don't think this is a bug with gnome-pilot, per se. It's just that it doesn't sit in the tray and listen for a connection.

Same bit with the scripts here - you have to invoke the script to get the computer listening. I haven't put time into making this sit in memory ... maybe a later project. Insert standard "not my fault if it kills your data" ... do lots of backups, read the pilot-xfer man pages. Hope this helps.

**pilot_backup.sh**

```
#!/bin/bash

if [ -z $1 ]
then
echo -ne "\nBacking up palm pilot to a directory with the current date and time:"

#get today's date and this moment's time stamp
BackupDir=`date +"%Y%m%d_%H:%M"`

#make a unique directory for this backup
if mkdir $BackupDir
then
 #do nothing ... need to fix this so that the error msg is an exception.
 echo
else
 echo -e "\n\nError making the backup directory. Do you have permission to make a directory here?\n"
 exit 2
fi

echo -e "\tCreated directory named $BackupDir.\n"
echo -e "Attempting backup. Press hotsync button to begin."
pilot-xfer --port usb: --backup $BackupDir

else
echo -e "Attempting to sync into directory $1. Press hotsync button to begin."
pilot-xfer --port usb: --sync $1
fi


exit 0
```

**pilot_restore.sh**

```
#!/bin/bash

#if no args ... exit error
#test to see if the first command line argument is null/empty
if [ -z $1 ]
then
echo -e "\nUsage: palm_restore.sh [source directory]\n"
exit 2
fi

echo -e "\nAttempting to restore from $1."
pilot-xfer --port usb: --install $1/*.*

exit 0
```

---

### Post by dragos240 on 2008-12-21
> **dentonlt said:**
> Sorry you didn't find the answer you wanted, (!). I normally don't show up here, but have had similar problems with gnome-pilot.

You probably know that gnome-pilot is just a wrapper for pilot-xfer and some other command-line tools. Since I had the same problem as you, I put together two scripts for syncing - one to back up, one to restore. Functional, not pretty.

I don't believe gnome-pilot is set up as a daemon to 'listen' for the palm sync/attachment. You have to invoke gnome-pilot first. I had luck by opening the gnome-pilot settings window, then pressing hotsync on the palm. Otherwise, the hotsync wouldn't get recognized. I don't think this is a bug with gnome-pilot, per se. It's just that it doesn't sit in the tray and listen for a connection.

Same bit with the scripts here - you have to invoke the script to get the computer listening. I haven't put time into making this sit in memory ... maybe a later project. Insert standard "not my fault if it kills your data" ... do lots of backups, read the pilot-xfer man pages. Hope this helps.

**pilot_backup.sh**

```
#!/bin/bash

if [ -z $1 ]
then
echo -ne "\nBacking up palm pilot to a directory with the current date and time:"

#get today's date and this moment's time stamp
BackupDir=`date +"%Y%m%d_%H:%M"`

#make a unique directory for this backup
if mkdir $BackupDir
then
 #do nothing ... need to fix this so that the error msg is an exception.
 echo
else
 echo -e "\n\nError making the backup directory. Do you have permission to make a directory here?\n"
 exit 2
fi

echo -e "\tCreated directory named $BackupDir.\n"
echo -e "Attempting backup. Press hotsync button to begin."
pilot-xfer --port usb: --backup $BackupDir

else
echo -e "Attempting to sync into directory $1. Press hotsync button to begin."
pilot-xfer --port usb: --sync $1
fi


exit 0
```**pilot_restore.sh**

```
#!/bin/bash

#if no args ... exit error
#test to see if the first command line argument is null/empty
if [ -z $1 ]
then
echo -e "\nUsage: palm_restore.sh [source directory]\n"
exit 2
fi

echo -e "\nAttempting to restore from $1."
pilot-xfer --port usb: --install $1/*.*

exit 0
```

It hotsync'ed perfectly now, with those shell files. Thank you, now i'm going to see if gnome pilot recognize. Thanks for showing up, cause i hate going into my vista partition just to hotsync.

I wish you the best of luck for whatever your doing,
sincerely,
Dragos240

---

