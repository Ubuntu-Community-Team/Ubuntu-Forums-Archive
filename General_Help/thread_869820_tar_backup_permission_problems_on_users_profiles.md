---
title: "tar backup permission problems on users profiles"
date: 2008-07-25
forum: General Help
---

### Post by beaker15 on 2008-07-25
Hi
I have an Ubuntu (Gutsy) server which i'm trying to back up. It's working as Samba domain controller for about 15 Wnidows XP clients. I also have a 500GB USB removable hard drive which i want to backup onto. 

OK so i followed the guide from the tutorials forum and created a .tgz file onto the USB drive but its the restore i'm having problems with. Again following the guide, it starts to unzip but encounters problems in the users profiles and home folders (yes i ran the command as root). Errors are along the lines of 
'Cannot change ownership to UID 1002, GID 1011. Operation not permitted' for files in the users profiles

and 

/home/Mark: Directory renamed before its status could be extracted
/hmoe/Simon: Directory renamed before its status could be extracted
/home/Mike: Directory renamed before its status could be extracted

etc. for the home dirs.

This is just a test restore i'm trying by the way so i'm restoring it into another folder i created on the USB drive, there's plenty of space. 

any ideas? thanks in advance.

PS will it be a problem that the filesystem i'm trying to backup is ext3 and the USB drive i'm saving it onto and doing a test restore into is VFAT?

---

### Post by dcstar on 2008-07-25
> **beaker15 said:**
> 
........
OK so i followed the guide from the tutorials forum and created a .tgz file onto the USB drive but its the restore i'm having problems with. Again following the guide, it starts to unzip but encounters problems in the users profiles and home folders (yes i ran the command as root). Errors are along the lines of 
'Cannot change ownership to UID 1002, GID 1011. Operation not permitted' for files in the users profiles
........
any ideas? thanks in advance.
........

Unless User Accounts with the same UID and Group Accounts with a GID exist in the system you are restoring them on, then I think that may be the outcome.

I don't think that Linux can use credentials that don't exist.

---

### Post by Yannick Le Saint kyncani on 2008-07-25
> **beaker15 said:**
> PS will it be a problem that the filesystem i'm trying to backup is ext3 and the USB drive i'm saving it onto and doing a test restore into is VFAT?

Yep, that's exactly it. Tar cannot restore uids and gids because the vfat filesystem does not support these features.

---

### Post by beaker15 on 2008-07-25
ok cool, so if i change the filesystem on the USB drive to ext3 it should work right? It doesn't matter if the data gets wiped because the backup i made is the only thing on it

---

### Post by Yannick Le Saint kyncani on 2008-07-25
Yep, it should work. As a side note, when you will have to restore a tar backup from another system, say, a livecd, don't forget to use --numeric-owner.

---

### Post by beaker15 on 2008-07-29
thanks. I needed to look that up and found that (as you know) this means tar uses UID/GID numbers rather than names

just out of curiosity, why do i need to do this? or is it just best practice

Thanks for all the help
:D

---

### Post by Yannick Le Saint kyncani on 2008-07-29
Without it, tar will adjust uids/gids to the currently running system. For example :

- System being backuped : group mysql is gid 135, group backuppc is gid 137.

- Restoring backup from another system, group mysql is gid 137, backuppc is gid 142.

- Tar will use names rather than numeric id's, so mysql's files are converted from 135 to 137 and backuppc's from 137 to 142.

- You boot in your "restored" system, files numbered 137 which were mysql files are now backuppc's, and files numbered 142 which were backuppc's now just appear to belong to group 142, without any name translation because group 142 does not exist.

- You realise your mistake and have to restore your backup again using --numeric-id.

---

### Post by beaker15 on 2008-07-30
That's awesome! thanks a lot

:guitar:


PS it worked!

---

