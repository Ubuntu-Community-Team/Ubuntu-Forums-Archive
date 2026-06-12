---
title: "Backup Options Question"
date: 2008-09-24
forum: General Help
---

### Post by lledurt on 2008-09-24
I have a computer I use as a file server using ntfs and smb.  It contains about 300-500GB of data.

I like to do occasional backups to a NAS drive but it seems slow.

I just purchases a dew hard drive and KF-1000-BK hard drive rack for faster backups.

I now see I have a couple of new options for backup's and would like some advice.

1.  RAID 1 to server dive and my hotswap drive.  For an occasional backup, pull one drive (backup image) and replace with a new one then sync the RAID.  Will this provide me a good backup?  Will it be faster then the other options? Is the backup image mountable to a different computer even though it was part of a RAID?

2.  Do a dd or cp or rsync to the drive.  This is basically what I do now but to a NAS and it seems to take forever. 

I also like to backup my home directories on my network.  This will woek with rsync and cp but not dd.  Is dd faster?  Is it worth using dd for my server then cp or rsync for the home directories?

One more question.  Will compressing my data via a tar.gz make the process faster or slower?  With the price of hard drives it seems like speed and convenience is more important.

I would love your opinions.  I realize there are more than one good answer, but would love the advice.

P.J.

---

### Post by russlar on 2008-09-24
dd does a block-by-block dump of your partition - not the greatest for backing up /home.

I use rsync and tar for my backups. Below are my usual commands

```
cd /home
tar -cvf homebu.tar ./russlar
gzip homebu.tar
rsync -av homebu.tar.gz /path/to/budrive/
```

---

### Post by bingoUV on 2008-09-24
> **lledurt said:**
> 

1.  RAID 1 to server dive and my hotswap drive.  For an occasional backup, pull one drive (backup image) and replace with a new one then sync the RAID.  Will this provide me a good backup?  Will it be faster then the other options? Is the backup image mountable to a different computer even though it was part of a RAID?


RAID will need to be rebuilt everytime you do this, and the system will be awfully slow for this time. At this time, there is a higher usage of hard disk, and so hard disk failure is more likely. You will understand that this is the most critical time when a hard disk failure is most undesirable.

> **lledurt said:**
> 
I also like to backup my home directories on my network.  This will woek with rsync and cp but not dd.  Is dd faster?  Is it worth using dd for my server then cp or rsync for the home directories?

One more question.  Will compressing my data via a tar.gz make the process faster or slower?  With the price of hard drives it seems like speed and convenience is more important.


dd is not faster. It doesn't work across a network anyway (unless you  mount the filesystem containing the device). Compressing will not make it much faster. Compressing will make the job of rsync difficult. Remember, rsync is supposed to be efficient backup. I.e. it transfers only the data that is really required to be sent. If you change just a single byte, rsync does not send the whole file across the network. It sends only the information enough to rebuild the file on the remote location.

Install rsnapshot, and read its man page. I think you will like it.

---

