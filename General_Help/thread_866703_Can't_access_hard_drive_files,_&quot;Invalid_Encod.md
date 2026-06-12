---
title: "Can't access hard drive files, &quot;Invalid Encoding&quot;"
date: 2008-07-22
forum: General Help
---

### Post by SRTS on 2008-07-22
Hi, I got a hard disk drive (ext3) where I copied a lot of files from windows over. Now Ubuntu can't handle some filenames appearently, and just shows some garbage mixed in the filename (where the special characters were supposedly) followed by a tag saying "Invalid Encoding".

The problem is: I can't even delete these files anymore. If anyone just tells me how I can get RID of them I'll already be happy. Currently, lots of folders are spammed with these files and I have no way of accessing them. Help please!

edit: I ran "fsck" on it, but it finished within a SPLIT SECOND, claiming everything was ok.. rotfl. I thought it was more like scandisk and could fix file problems. If anyone knows of a working scandisk/chkdsk tool for Ubuntu, that might also help.

---

### Post by SRTS on 2008-07-22
Anyone have a solution? I can't believe these files will be unremovable forever until I format the whole drive (which isn't an option).

---

### Post by Shunsuke_01 on 2008-07-22
> **SRTS said:**
> Anyone have a solution? I can't believe these files will be unremovable forever until I format the whole drive (which isn't an option).

Where are these folders?

If they are in your home drive you could try:

rm -rf /home/<userhere>/<foldername>

---

### Post by SRTS on 2008-07-22
Ok that worked appearently, thanks :)
Funny that the normal file manager can't handle it though.

---

### Post by danwood76 on 2008-07-22
You can force drives to be mounted with different encoding schemes to allow unicode and the like.
Have a look into fstab options.

---

