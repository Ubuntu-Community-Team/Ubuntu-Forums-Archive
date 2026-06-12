---
title: "[SOLVED] dd to backup a partition?"
date: 2008-10-20
forum: General Help
---

### Post by alphaniner on 2008-10-20
Can I use dd to backup (and restore) just a partition from an HDD?  I would like to make a backup of my Windows installation immediately after install so I can restore it if it gets borked and not have to worry about re-validation and such.  Is this doable?

---

### Post by Seq on 2008-10-20
> **alphaniner said:**
> Can I use dd to backup (and restore) just a partition from an HDD?  I would like to make a backup of my Windows installation immediately after install so I can restore it if it gets borked and not have to worry about re-validation and such.  Is this doable?

Yes, but it would be much more flexible to use something like 'partimage' as it will give you a much smaller image (backing up only data). The downside is that you need partimage to restore it as well (There are plenty of livecds around -- I like sysrescuecd)

---

### Post by Titan8990 on 2008-10-20
I was under the impression the partimage was just a GUI for dd. Is that incorrect?

---

### Post by alphaniner on 2008-10-20
I may give partimage a try, but according to the info in the Ubu repos, NTFS support is still only experimental.  I was thinking a dd image would be highly compressible if most of the space was free, but in retrospect I realized it's not quite that simple ;)

---

### Post by Seq on 2008-10-20
> **alphaniner said:**
> I may give partimage a try, but according to the info in the Ubu repos, NTFS support is still only experimental.  I was thinking a dd image would be highly compressible if most of the space was free, but in retrospect I realized it's not quite that simple ;)

Most of your space is "free" as far as the file system is concerned, but will be mostly random crap rather than zeroes, so it may or may not compress well (depending on what the original data was). partimage does gzip and bzip compression on images as well, so regardless of the actual achieved ratio, less input == less output :)

I've used partimage at work for backups for a while with system rescue cd and havent had any problems (partimage on ntfs while using a hardy livecd fails every time).

---

### Post by alphaniner on 2008-10-20
> **Seq said:**
> Most of your space is "free" as far as the file system is concerned, but will be mostly random crap rather than zeroes, so it may or may not compress well...

That's exactly what I was talking about.  And I should have known better, considering my recent adventures in file recovery...

When you mention sysrescuecd, are you referring to [http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")?  And with that you have been able to backup/restore NTFS partitions?

---

### Post by Seq on 2008-10-20
> **alphaniner said:**
> That's exactly what I was talking about.  And I should have known better, considering my recent adventures in file recovery...

When you mention sysrescuecd, are you referring to [http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")?  And with that you have been able to backup/restore NTFS partitions?

Yes. I'm using the 1.0.0 disc (with Window Maker -- WOO!) instead of the current. I did a weekly partimage of my work laptop, and actually used that when I got a new hard disk for it.

The only downside is that you can't browse the archive or loop-mount it to get particular files out, you need to restore it to something. :(

---

### Post by alphaniner on 2008-10-20
Do you use 1.0.0 because it includes Window Maker and later versions don't, or for some other reason?  And what is Window Maker anyway?

---

### Post by alphaniner on 2008-10-20
So I bit the bullet and tried partimage using sysrescuecd (from a USB stick, even!).  I imaged the partition, re-formatted it with ext3, then restored.  I was pretty thrilled when I rebooted and Windows loaded.  But then I opened PerfectDisk, out of curiosity about how fragmented the partition would be.  It wasn't bad, but I went ahead and defragged anyway.  Alas! there was a problem.  Where before only a few 'blocks' (not literally vis-a-vis HDD geometry; it's how PD displays disk usage) were classified as 'Boot' type files, now the a large portion of them do.  Honestly, I'm not sure of the ramifications of this, but it doesn't make me comfortable.  It's disappointing, because the operations (saving and restoring the partition) were super fast.  I figure I'll give it another try, but I just realized my copy of Fable II arrived earlier today!  Huzzah!

---

### Post by Seq on 2008-10-21
> **alphaniner said:**
> Do you use 1.0.0 because it includes Window Maker and later versions don't, or for some other reason?  And what is Window Maker anyway?

Yes, specifically because of this.

> **alphaniner said:**
> So I bit the bullet and tried partimage using sysrescuecd (from a USB stick, even!).  I imaged the partition, re-formatted it with ext3, then restored.  I was pretty thrilled when I rebooted and Windows loaded.  But then I opened PerfectDisk, out of curiosity about how fragmented the partition would be.  It wasn't bad, but I went ahead and defragged anyway.  Alas! there was a problem.  Where before only a few 'blocks' (not literally vis-a-vis HDD geometry; it's how PD displays disk usage) were classified as 'Boot' type files, now the a large portion of them do.  Honestly, I'm not sure of the ramifications of this, but it doesn't make me comfortable.  It's disappointing, because the operations (saving and restoring the partition) were super fast.  I figure I'll give it another try, but I just realized my copy of Fable II arrived earlier today!  Huzzah!

I have never used perfect disk. I usually would let windows defrag itself. Is there an advantage to perfectdisk?

---

### Post by alphaniner on 2008-10-21
It has been years since I used Windows defrag.  But one of the reasons I switched to PD is because it consolidates free space as well as defragging.  It stacks all the files to the 'front' of the drive so you usually end up with just one or two huge blocks of free space.  Also, it organizes the files by the date modified.  This way stuff that is 'new' will always go to the end of the stack, rather than displacing older files when defragging.  This is primarily beneficial if the stuff is not going to be around long.  These two features are why I use it.

---

### Post by alphaniner on 2008-10-24
I just discovered a utility called ntfsclone - also on the sysrescuecd - which does the exact same thing as partimage but is designed specifically for, you guessed it, NTFS.  The image files come out about the same size as those of partimage.  Haven't tried a restore yet.

---

### Post by Seq on 2008-10-24
> **alphaniner said:**
> I just discovered a utility called ntfsclone - also on the sysrescuecd - which does the exact same thing as partimage but is designed specifically for, you guessed it, NTFS.  The image files come out about the same size as those of partimage.  Haven't tried a restore yet.

I believe partimage actually utilizes that, and adds on the optional server comonent, splitting for volumes, gzip, etc.

Are you able to mount that image as a loopback filesystem and pull individual files out? That is the biggest missed feature of partimage

---

### Post by alphaniner on 2008-10-24
> **Seq said:**
> Are you able to mount that image as a loopback filesystem and pull individual files out?

ntfsclone can create two types of image files.  The kind I made and referred to in the last post can not be mounted.  The other kind is a 'sparse file' type image which can be mounted.  I'll endavour to explain what a sparse file is in case you don't know.  I sure as heck didn't before reading the ntfsclone man pages.

A sparse file is a weird type of file that is full of holes, apparently.  I went ahead and tried creating this type of image.  When I do a 'ls -lh' on the directory that contains it, it shows up as 11GB.  But a 'du -h' on the file shows it as only 3.2GB.  And 'df -h' shows the partition which contains nothing but that file as only having 3.3GB used. The main downside of sparse files is that they aren't supported by cd/dvd filesystems and they aren't handled well by compression tools.  And presumably if you were to copy such a file you would have to process the entire 11GB.  I assume I could put another 11 or so gigs of 'normal' files on this partition (which is 15GB) but I don't know if I could have three more sparse file images of the same size.  I accidentally tried to make the image in / and based on the error I got I think it could exist on a partition of only ~3.3GB.  Again, this all comes from a whopping 15 minutes of experience and reading the ntfsclone man pages, so take it with a grain of salt if you take it at all.

Update:

I was able to create one of the sparse image files on a 4GB partition.  Thing is, I'm not sure it is possible to use the utility to restore a partition from one of these files.  The man pages only mention restoring from the other type (called special image format) and that method does not work with one of the sparse images.

Update 2:

For the record, there is definitely a difference between ntfsclone and partimage.  After restore, I ran PerfectDisk and the data on my drive was distributed exactly as it was when I imaged it.  Most importantly, none of the files had been 'transformed' like they were when I used partimage.  Thanks again for pointing me to sysrescuecd though, it's a fantastic tool.

---

