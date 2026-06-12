---
title: "Hard disk recovery"
date: 2012-01-16
forum: Hardware
---

### Post by coreychbt8295 on 2012-01-16
hello, i need help recovering lost data on a usb drive, it was ntfs then stopped working.  i reformatted it several times to try to recover the files.  nothing was written prior to the drive issue.  ive tried gnu parted gpart, scalpel, foremost, testdisk.  any help is appreciated

---

### Post by hansdown on 2012-01-16
Hi, coreychbt8295.

Reformatting tends to destroy the data.

Will the usb mount at all?

---

### Post by coreychbt8295 on 2012-01-17
ya, it mounts just fine now

---

### Post by hansdown on 2012-01-17
Any data on it now?

---

### Post by Mark Phelps on 2012-01-17
Reformatting it WILL allow it to mount again, as it writes a new partition table, but that erased the OLD partition table.

However, even though the table has been rewritten, the old files are mostly still there.

You might be able to use data recovery apps to get the files and directories back.

---

### Post by coreychbt8295 on 2012-01-17
no, no data

---

### Post by coreychbt8295 on 2012-01-17
ill probably just redownload the media that i lost

---

### Post by dbarreth on 2012-01-18
Thsi program will be able to locate the old data in the lost partiotion and copy it out from there.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

I'ts opensource, this particular program can even restore the old partition if youre lucky. Used it several times, and in several ways it's better than some commercial software out there. (have med quite some data recovery's through out the years for several costumers)

I've just run this particular program through windows though, but they have support for linux aswell. The wiki is very good and contains good tips and guide to use the program for different tasks.

---

### Post by coreychbt8295 on 2012-01-18
ive tried test disk, too complicated/didnt work

---

### Post by Grenage on 2012-01-18
Getdataback for NTFS is probably the best software I've seen for NTFS recovery.  It does however cost money.

Testdisk is also very good, but you'll need to read some guides as you go, if you don't know what you're doing.

Failing that, you'll need to be a lot more descriptive than "too complicated/didn't work".

---

### Post by coffeecat on 2012-01-18
> **coreychbt8295 said:**
> ive tried test disk, too complicated/didnt work

@coreychbt8295, since you've reformatted the partition, testdisk is not appropriate. Testdisk is for recovering lost partitions, not lost data. Your partition is not lost, simply that the filesystem has been reformatted, hence the lost data.

One option is photorec which comes with testdisk. Have a look at this guide:

[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

Ignore the live CD bit - you can run photorec from your permanent Ubuntu installation - and scroll down past the testdisk instructions. The photorec instructions are not quite halfway down.

Having said that, photorec is not easy to use and the recovered filenames are not the original ones. Because of that, even though photorec is very effective at recovering lost files, you may find Grenage's suggestion better.

---

### Post by Mark Phelps on 2012-01-18
Runtime Software produces both GetDataBack and RecoverMyFiles -- but they both run on Windows.  You can download trial versions to Windows PCs, and while those will scan and find deleted files and directories, they won't actually restore them.  You have to purchase the products to do that.  But, if you can connect your disk to a Windows PC, you can at least see if their products detect your deleted directories and files.

---

### Post by coreychbt8295 on 2012-01-18
i mean that either i didnt do something right, or it simply couldnt find old partitions

---

### Post by coreychbt8295 on 2012-01-18
thank you everyone for the support, i am just going to redownload.   this really is a great forum to post questions in!:D

---

