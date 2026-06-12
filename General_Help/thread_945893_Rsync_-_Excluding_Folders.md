---
title: "Rsync - Excluding Folders"
date: 2008-10-12
forum: General Help
---

### Post by raywood on 2008-10-12
I'm using Hardy on a WinXP dual boot system.

I'm learning to use rsync to back up a data drive to an external drive.  Here's what I've got in my script at this point:

```
rsync -vshlEPtrip --del --delete-excluded --force \
--exclude=RECYCLER \
--exclude="System Volume Information" \
/media/DATA /media/186GB
```

The source drive is NTFS, so it has those two folders (RECYCLER and System Volume Information) that Windows XP installs automatically.  I don't need to back them up.  But my exclude command doesn't seem to be working.  I'm guessing it doesn't apply to folders, only to files.

I'm also not seeing any verbose output, or anything else.  The only way I can tell whether the thing is done is to observe whether the hard drive seems to become inactive.  What am I doing wrong?  Also, do my command-line options make sense?  Thanks!

---

### Post by qpieus on 2008-10-12
Hmmm, as far as I know, the exclude= option works for directories too. A few questions: 
What does get rsync'd, if anything, when you run the command? Or does the whole command fail (i.e, nothing is transferred)?
Do the RECYCLER and System Volume Information directories exist directly under /media/DATA ?
You could try to put the directories you want to exclude into a file and use the --exclude-from=FILE option instead. If you use this, just put the 2 directories in a text file like so:```
RECYCLER
System Volume Information
```
and put the file name in place of FILE in the option syntax.

I suspect the issue lies with the source drive being NTFS, but that's just a guess. I don't have any NTFS disks to try it out on. I use rsync to synchronize my FAT32 formatted IPOD and rsync used to re-transfer everything because the fat32 filesystem didn't record accurate enough file date/time stamps. (I solved that by using the --modify-window=1 option, FWIW)

---

