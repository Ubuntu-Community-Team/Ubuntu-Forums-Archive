---
title: "Reformatting a 750gb external WD Mybook"
date: 2008-04-29
forum: Hardware
---

### Post by einnar on 2008-04-29
I'm debating reformatting my 750GB External WD Mybook....

I'd like to put something like ext3 on it, so I can better use permissions. Unfortunately, it's about half full, and I don't have a place to move everything temporarily as I'm away from home with it.

My questions are:

1) Is it wise to do this, or should I just leave it as is? I realize that reformatting it means I can't use it on windows machines, but that doesn't bother me.

2) Can I use gparted to :
 - resize the existing partition to about 1/2 the disk.
 - format the remaining area in ext3
 - copy my files from the fat32 partition to the ext3
 - remove the fat32
 - resize the ext3 to the full disk space

3) is ext3 the format to use?

Thanks!

---

### Post by einnar on 2008-04-29
bump

---

### Post by einnar on 2008-04-30
Anyone at all?

---

### Post by bigken on 2008-04-30
I would imagine you can do this with gparted

---

### Post by einnar on 2008-04-30
Thanks.

What file system would you use?
Is my proposed method something that will work, or will I lose data?

---

### Post by bigken on 2008-04-30
it should work personally I would use fat32 so you can read files in windows ect I would also create a small ntfs partition for large files such as video ect 


its a dangerous thing messing with partitions what you are trying to do should workbut again I would not take the risk without backing up my data 1st

---

