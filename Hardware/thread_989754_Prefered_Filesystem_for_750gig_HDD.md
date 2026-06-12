---
title: "Prefered Filesystem for 750gig HDD"
date: 2008-11-21
forum: Hardware
---

### Post by skozzy on 2008-11-21
There is a few format/filesystems I can format a drive to, but which one offers the best speed for reading writing large files. At the moment I have been using NTFS from Window, but in lunix it take 8 hour to read a full 750gig to another 750gig drive, where windows does it in under half the time.

So if I want to read from a 750gig NTFS formatted drive and save to another 750gig drive, what file system should I use, ext2 etx3 xfs etc... I don't understand all the different linux formats.

---

### Post by __Ryan__ on 2008-11-22
Your best shot is ext3.  It is by far the most common and very well supported.

---

### Post by skozzy on 2008-11-22
I selected ext3 and I was a little shocked that nearly 70gig was preallcoated but to what I don't know. It did generate a lost+found folder, maybe it reserved space, but that is a lot to do without. I know NTFS (the source drive I was copying data from) had more space for the same size drive.

---

### Post by taurus on 2008-11-22
As default, 5% of your total disk space is reserved for root in case you fill up your drive, you can still log in to delete files.  However, there is no safeguard in windows so if you fill up your disk space, you are a sitting duck in windows.  And since you use that drive for storage, you don't need to reserve it if you don't want to.  You can use the tune2fs command to reset it back to 0.

```
sudo tune2fs -m 0 **/dev/sdb1** (or whatever the device for that harddrive)
```

---

### Post by skozzy on 2008-11-24
Thanks for that command, it will be used on my data drives for sure.

---

