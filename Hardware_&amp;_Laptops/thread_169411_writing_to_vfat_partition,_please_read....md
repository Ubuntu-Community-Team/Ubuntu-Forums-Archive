---
title: "writing to vfat partition, please read..."
date: 2006-05-02
forum: Hardware &amp; Laptops
---

### Post by rmetz on 2006-05-02
Here is some background info.  I currently have Ubuntu Dapper dual booted with WinXP on a 2GHz 256MB Ram dual HD system.  I have WinXP on hda and Dapper on hdb2-5.  Here is my question.  I have hdb1 set up as a fat32 partition so that I can share documents between Linux and WinXP.  When I load Ubuntu it automatically recognizes hdb1 and allows me to VIEW the files, but it will not allow me to write to the partition.  I changed my fstab to look like this for that partition:

/dev/hdb1  /media/hdb1  vfat  user,fmask=0111,dmask=0000  0    0

However, when I remount the filesystem, nothing changes.  I can still view the files, but I can not write.  I am relatively new to linux, so please bear with my stupidity.  When I look at the properties of the partition it says that I am not the owner of the drive.  Does that have something to do with it?  I have tried sudo chmod and everything else that I am aware of, but no change.  I could really use some expert advice on this problem.  Thank you for your time.

---

### Post by tonyr on 2006-05-02
Just a suggestion, based on watching the forum for awhile.  Try
changing **user** to **defaults**.  The **user** option 
is generally used for removeable media.

You could also try
```

/dev/hdb1 /media/hdb1 vfat defaults,rw,umask=0000 0 0

```

---

### Post by rmetz on 2006-05-03
thank you for the info.  it turned out that I didn't have to change anything.  I tried to remount the filesystem and it didn't work, but when I restarted the computer it worked fine.  I don't know why remounting didn't work, but I am glad that I have it working now.  Thanks so much for your help.

---

