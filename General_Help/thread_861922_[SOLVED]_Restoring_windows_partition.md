---
title: "[SOLVED] Restoring windows partition"
date: 2008-07-17
forum: General Help
---

### Post by sab_fossy on 2008-07-17
Hi all

I had installed ubuntu through wubi allowing 30Gb. Then I decided to remove ubuntu and have it old way!
Using the uninstaller under add/remove program in windows i did uninstall ubuntu. but the problem is, that windows has not freed up 30gb. when I add up all the files and folders (inc. hidden) + free space it is still 30GB short!
Is there away to manually remove the wubi partition? I have tried chkdsk for windows xp ntfs filesystem fixing, but no error message.

Thanks in advance for your help

---

### Post by ago on 2008-07-17
If you do not have a /ubuntu directory, make sure there are no hidden files called c:\found.000*. You need to change the settings in windows explorer to see hidden files.

---

### Post by sab_fossy on 2008-07-17
Thanks for your prompt respond. there is no \ubuntu folder and alos no c:\foun...file. It has to do something with the file system. As I mentioned the total size of all the files + folders (include hidden files and folder) does not refelct the used volume shown in windows. The only thing I can think of, the uninstaller still did not restore the file system to normal ntfs.

i tried to read the partitions using Virtual Volumes. It does not appear there either!

---

### Post by ago on 2008-07-17
> **sab_fossy said:**
> The only thing I can think of, the uninstaller still did not restore the file system to normal ntfs.

The uninstaller simply deletes Wubi files and directories, partitions/filesystems are not modified in any way. The ubuntu "partition" is simply a file within windows. The delete command is done via nsis, but that ultimately is a standard win api call.

---

### Post by sab_fossy on 2008-07-17
Many thanks for your reply.
I am doing a C:\ Disk Cleanup. So far freed up 4GB!!!
Let you know if that was the problem.
Cheers
Sab

---

### Post by sab_fossy on 2008-07-17
Nope,

Still 30GB is missing!

---

### Post by ago on 2008-07-17
Run chkdsk /r on the partition where you installed wubi
Then look for the found.000 files? 
In windows explorer tools > folder options > view set to show hidden and system files

---

### Post by sab_fossy on 2008-07-17
Thanks mate! I have done all those, if you read my posts.
I guess I have to reinstall windows, and go back to good old Gentoo. At least they won't treat you like a dumb!:)

---

### Post by ago on 2008-07-17
Did you also run chkdsk /r?

---

### Post by sab_fossy on 2008-07-17
/f for fix it i did last night and now it is doing /r per ur suggestion. 
your help is greatly appreciated.

---

### Post by sab_fossy on 2008-07-17
Sorted!:guitar:
FOSS bless you!
Many many many thanks!
Sab

---

### Post by diilbert on 2008-07-17
What was the issue?

---

### Post by sab_fossy on 2008-07-17
chkdsk /f did not fix it. But /r worked.

just off the record, fsck m$ :)

---

