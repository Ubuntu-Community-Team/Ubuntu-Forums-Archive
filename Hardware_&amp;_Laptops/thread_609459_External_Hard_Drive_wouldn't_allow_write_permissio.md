---
title: "External Hard Drive wouldn't allow write permissions"
date: 2007-11-11
forum: Hardware &amp; Laptops
---

### Post by bharris25 on 2007-11-11
I have a Seagate Freeagent 160 gb external hard drive and it was working just fine but for some reason it would no longer allow me to write to it.  The permissions were set to my user name and I could actually create a new folder to it if I did it right when it first mounted but then if you entered a sub folder all the folders would get a lock on them.  When you would back out to the root folders they would have no lock but when you would single click on them one by one just to highlight them the lock would appear, I'm not sure if it was a bug or a problem with the drive because I had recently backed up all info on the drive and it was not limited to Gutsy, I also could not write to the drive with Mint 3.0 that I have dual booted, same situation except that the permissions on the Mint said that it was root.  After I used Gparted to reformat the drive to fat32 I found that only the previously unused portion showed up when I the window which was only 48gb out of 160.  I reformatted several times but it kept saying that there was only 48gb of free space, I tried fat32, ntfs, and ext3, none worked.  Finally I formatted half of the drive with ntfs, and the other half with fat32 and then it all showed up when mounted but I found that I could still not write to the ntfs partition but could now write to the fat32 side.  I reformatted one more time to fat32 and that time all the free space showed up and I could write to it :guitar:  If anyone could let me know why this happened I would appreciate it, I feel it is a bug with the ntfs writing that comes with gutsy but I suppose it could have been the hard drive since it was also happening with Mint 3.0.:confused:

---

