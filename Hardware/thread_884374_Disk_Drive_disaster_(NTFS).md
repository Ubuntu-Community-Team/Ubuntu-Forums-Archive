---
title: "Disk Drive disaster (NTFS)"
date: 2008-08-08
forum: Hardware
---

### Post by quazi on 2008-08-08
So I have an NTFS external harddrive that I've used to store my multimedia files.  I started deleting tons of files from it (under Ubuntu) to clear up some space and then I/O errors started cropping up all over the place.  I backed up what I could and then stuck it on a Windows machine to run chkdsk.

Well, it doesn't even show up under windows, USB errors crop up when I connect it and Disk Manager doesn't acknowledge it.  Putting it back onto linux (to just completely wipe the disk) doesn't work either at this point, giving me the error Mount is denied because NTFS is marked to be in use.

My solution was simply to boot into linux and run gparted to delete the NTFS partition (at the time I was worried I was somehow doing permanent damage to my disk).  

Is writing to NTFS still this unstable?  Because it was enabled by default when I plugged my disks in, I assumed it wouldn't have this many issues.  Sorry for the somewhat rambling post.

---

### Post by falcon61102 on 2008-08-08
NTFS normally isn't a problem anymore.

To mount your drive you can force mount it which will make Ubuntu overwrite the sector saying that it was still mounted in an NTFS enviornment.  And example would be:
```
sudo mkdir /media/External
sudo mount /dev/sdb1 /media/External -f
```
What this is going to do is creat a mountpoint and then force mount your drive.  You just need to replace /dev/sdb1 with the appropriate partition name for you USB drive.  If you are unsure about that, use:
```
sudo fdisk -l
```

---

### Post by quazi on 2008-08-08
> **falcon61102 said:**
> NTFS normally isn't a problem anymore.

To mount your drive you can force mount it which will make Ubuntu overwrite the sector saying that it was still mounted in an NTFS enviornment.  And example would be:
```
sudo mkdir /media/External
sudo mount /dev/sdb1 /media/External -f
```
What this is going to do is creat a mountpoint and then force mount your drive.  You just need to replace /dev/sdb1 with the appropriate partition name for you USB drive.  If you are unsure about that, use:
```
sudo fdisk -l
```

Tried doing that (sorry, shoulda mentioned it) after I saw it in the error message.  The terminal stalled when I entered that and I had to hit CTRL+C to get out of it.  Also as an update, the reformat didn't work.  I tried reformatting it as fat in linux and after I mounted the drive to look at it and ran an ls command, there were hundreds of I/O errors and the terminal text "got all funky" so as to be unusable.  I'm currently trying to zero out the disk with the command: dd if=/dev/zero of=/dev/sdb bs=1M.

---

### Post by quazi on 2008-08-09
Well, I've come to the conclusion that either my external enclosure, or the drive itself is fried (haven't put the effort into sticking the drive into a desktop, took me about 10 minutes to take out the billion screws WD sticks into their externals).  

However, it's entirely possible (even likely) this has nothing to do with Ubuntu, it may just be coincidence it died shortly after I put on Linux.  This is the second WD MyBook drive I've gone through and my guess is the drive's are just very shoddy and its time at come.  Thanks for the help.

---

### Post by falcon61102 on 2008-08-09
Well, if you ever get around to getting the drive into your desktop and you find out it's not the drive, let us know and I'm sure somone can help you out with it.

---

