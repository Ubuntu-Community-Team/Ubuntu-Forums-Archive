---
title: "How to COMPLETELY FORMAT a Hard Drive?"
date: 2012-12-31
forum: Hardware
---

### Post by ByaTsuke on 2012-12-31
I have 2 hard drives at the moment.
1. Internal Laptop HDD - I have 2 partitions, one partitions works just fine, other don't, but I extracted all my datats from the one that doesn't.

2. I have an external 500gb HDD, which I am booting ubuntu from and have stored all my recovered files in there.

So now, I need to COMPLETELY wipe out, format and refresh my Internal HDD. which needs formatting because of the corrupt windows files that even block proper fresh windows 8 installation. 

HOW? I tried "DISKS" application but it gave me an error. 

I can use testdisk to copy files from the broken partition of y internal HDD, and access it, it's all visible on testdisk but how do I forcefully format and clean it?

Are there any softwares, commands or some tricks to do that?

---

### Post by adityamagadi on 2012-12-31
well you could do an rm -rf on the partition that you wanna wipe out , else you can use the gparted application in ubuntu.

---

### Post by ahallubuntu on 2012-12-31
Use DBAN (Darik's Boot And Nuke) CD to wipe the hard drive entirely, once you get everything you wanted off of it.  (You can use the "quick" erase to do one pass, otherwise it does three passes to securely erase data and takes 3X as long - probably several hours at least.)  Probably good to disconnect the USB drive before running DBAN to make sure you don't accidentally erase the wrong drive.

Once DBAN is done, check the drive's S.M.A.R.T. status.  If there are serious errors (e.g. Pending Sectors), the drive is bad and will need to be replaced.  You can check S.M.A.R.T. attributes with GSmartControl within Ubuntu or using the Parted Magic Linux Distro.

---

