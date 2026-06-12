---
title: "folder count difference in usb drive - rsync"
date: 2008-09-24
forum: General Help
---

### Post by candtalan on 2008-09-24
I back up a current set of files and folders in one tree by using rsync to a usb external hard drive.
This is a large set of files  - in this case, 327477 files in all. 
The same number of files exists on the usb hd at completion, however, the original tree properties (using dolphin) says 31228 folders while the completed usb hd set indicates 31153 - that is, approximately 70 fewer folders.

Both the original FS and the usb hd fs are ext3. 

the rsync commands I used were
rsync -rt --progress --stats /source  /destination

there were no errors stated in rsync at completion.

Any ideas why the different numbers of folders? I note the file count is the same.
tia

---

### Post by Peter09 on 2008-09-24
Is it counting hidden files?

---

### Post by vanadium on 2008-09-24
You probably should be using the -a (archive) switch to create a mirror backup copy. Add --delete to the options, and files in the destination that do not exist in the source will be deleted:

rsync -av --delete /source /destination

---

