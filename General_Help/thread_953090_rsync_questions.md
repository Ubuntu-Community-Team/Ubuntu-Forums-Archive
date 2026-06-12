---
title: "rsync questions"
date: 2008-10-19
forum: General Help
---

### Post by guitarj1d on 2008-10-19
I'm trying to use rsync to copy all of my finished torrent downloads to an external drive.  this is so I can continue seeding while still being able to organize my newly downloaded torrents.  so let's say my finished downloads is /downloads and the folder I want to copy to /media/external/incoming.  I used the command rsync -av /downloads /media/external/incoming.  everything is then backed up to the .../incoming folder.  however, when I then move those files out of .../incoming to my organizational tree and resync again, they are placed back in incoming.  is there a way to store which files have already been synced so it doesn't keep resyncing  if the .../incoming file is no longer there?

---

### Post by russlar on 2008-10-19
rsync -av **--delete** source destination

this will remove files from the destination if they no longer exist in the source.

---

### Post by guitarj1d on 2008-10-19
I want to keep the files in the source directory, so I can continue seeding.    It's the files in the destination directory that I want to move.  But I don't want them to keep reappearing every time I sync

---

### Post by unutbu on 2008-10-19
Is /media/external/incoming and the organizational tree on the same ext3 filesystem?

---

### Post by guitarj1d on 2008-10-19
correct.  it's on an external drive.  this way I can keep track of what has been organized while still seeding the original file

---

### Post by unutbu on 2008-10-19
Instead of *moving* files from /media/external/incoming to the organizational tree,
use hard links:
```

ln /media/external/incoming/afile /organizational/tree/afile
```

Hard links take up almost no additional space. 
You can therefore keep the files in /media/external/incoming forever so rsync won't 
repeatedly transfer them. For example:

```
mkdir test
cd test
dd if=/dev/zero of=big count=2000    # Make a 1MB file
du -sh .                             # Measure the size of the test directory
# 1008K	.
ln big big2
du -sh .
# 1008K	.                            # Notice the size of the directory is the same
ls -l
# total 2008
# -rw-r--r-- 2 hairdryer hairdryer 1024000 2008-10-19 23:22 big
# -rw-r--r-- 2 hairdryer hairdryer 1024000 2008-10-19 23:22 big2
```

big2 is just as good as a copy of big. You can delete big and big2 will still be there. 
You can delete big2 and big will still be there. 

Unlike a copy however, big2 essentially takes up no additional space, and if you modify one file, the other gets modified too.

---

### Post by guitarj1d on 2008-10-19
that's exactly what I was looking for.  is there anyway to have the source folder hard copy to the destination automatically?  so anytime a file is added to the source it creates a hard copy in the destination, completely bypassing rsync

---

### Post by unutbu on 2008-10-19
If I understand your situation correctly, /downloads is on an internal drive and incoming is on an external drive? In this case, unfortunately, you can not create hard links across filesystems. You have to copy using a tool like rsync.

Also, hard links are for files only. There are no hard links for directories (though that would be cool).

---

### Post by guitarj1d on 2008-10-19
ah, that probably won't work though because source and destination are on two different ext3 file systems

---

### Post by guitarj1d on 2008-10-19
ha, you posted right before I had that thought!   This gets me like 90 percent there, one reason I wanted to move the files from destination to tree is so I can tell which ones have already been organized.  because it takes up so much of my time

make sure the file is seeded sufficiently
make sure it has been categorized
then delete the original

doesn't seem like much, but with 100 plus torrents a week, my sundays are always filled up with this procedure

so if i have the file in two places, once I'm finished seeding I can just delete the file, knowing they're already backed up to the destination and ready to be organized

---

### Post by guitarj1d on 2008-10-20
I think the best solution would be to write a script that scans the source folder every hour, if it sees a file that has been modified within that hour it will copy to the destination folder.  now...all I have to do is brush up on my bash scripting

---

