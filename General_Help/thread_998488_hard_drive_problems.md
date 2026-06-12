---
title: "hard drive problems"
date: 2008-11-30
forum: General Help
---

### Post by kristiansuhl on 2008-11-30
Hello!

I have an external hard drive that I by mistake somehow made "unformated". It was never formated into a new filesystem, so the data should still be there intact.

It was originally a FAT32 drive that I created a while ago in ubuntu from scratch. The drive is physically perfectly ok and there was no "new" formatting done, I just sort of took away the formatting when I was doing some maintenance. I'm quite sure that the actual data is perfectly ok - it's just that neither ubuntu nor windows finds the drive anymore.

This little mishap was done when I was installing windows on a machine and by mistake made it into "unformated space" ready for formatting. 

My theory is that all the data is intact, I'm no expert but I guess that somehow I should be able to rescan it and recreate it. 

My question is this: Is it possible to do a recovery try in ubuntu? If yes - what program should I use?

---

### Post by falcon61102 on 2008-11-30
The first thing you want to do is to copy or make an image of the entire drive and then work with that imagine so that if you mess anything up, you won't lose your original data.  You can do this with:
```
sudo dd /source /destination
```

Replace /source with the drive partition designator which should be something like /dev/sdb1.  Replace destination with where you want to copy the entire drive to, you are going to need something that is at least as big as your external because the dd command will copy everything, even blank space.  Perferably you should have another external to copy to.

Also, through what process did you make the drive "unformatted" as that might help in figuring out how to get your data back?

---

### Post by kristiansuhl on 2008-12-01
You're right, I should do a backup! :-)

The unformatting was done in a stupid way by me unfortunately. I had to temporarily install windows and in the installation sequence when windows wanted to know where it should install itself I took away the partition of the external drive by mistake. I wanted to make room for the windows installation by taking away all the earlier partitions... and then I took away the external drive by accident. I did no new formatting of it though.

---

### Post by hyper_ch on 2008-12-01
there was only one partition on that harddrive?

---

### Post by lucasl on 2008-12-01
Try [Testdisk]("http://www.cgsecurity.org/wiki/TestDisk").
It's in the repos, and is pretty self explainitory.
Make sure you've backed up though.

---

### Post by kristiansuhl on 2008-12-01
> **hyper_ch said:**
> there was only one partition on that harddrive?


yes, there was only one partition, the FAT32 one, created in ubuntu. Is that good or bad? :-)

---

