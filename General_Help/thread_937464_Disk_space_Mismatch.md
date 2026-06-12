---
title: "Disk space Mismatch"
date: 2008-10-03
forum: General Help
---

### Post by windfix on 2008-10-03
I am running Hardy 8.04 on 4th gen Macbook Pro, dual boot to OSX via rEFIt.

For some reason, my 107 GB partition thinks it's almost full.  Partition editor shows only 2.5 GB free - and I have loaded only 15 GB of user files.

Oddly, Disk Analyzer shows the same 2.5 GB free, but says the filesystem is only 25 GB, 22.5 used.

What the heck happened to my free space and how can I reclaim it?  (I'm fairly new, but a tiny bit familiar command line, and do have access to a local linux guru - but he's stumped too).

---

### Post by AmyRose on 2008-10-03
Are you sure you have partitioned it correctly? What does the "df -h" command say about disk usage?

---

### Post by unutbu on 2008-10-03
Perhaps your trash is full.
Finding all the trash bins is a bit tricky. Here is a good guide:
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

When Disk Analyzer (baobab) is run as a normal user, it does not have the right permissions to look inside all directories on the system. In this case the space numbers it reports can be wrong -- or at least not relevant when considering the disk as a whole.

Another possibility is that you have an automatic system backup script/app running.
To find what is being a disk hog, perhaps the easiest way is to run baobab as root:
```

gksu baobab
```

Analyze the entire drive and browse the largest directories.

---

### Post by windfix on 2008-10-04
I'll give these suggestions a shot if I can boot again.  Now I've really hosed myself by making that partition un-bootable.  I tried running Hardy from CD and using partition editor to reduce my HFS partition (worked fine) and grow my linux partition (failed).  3 hours later, I got an operation failed message and can not boot.

I can see the files via Nautilus.  Tried running fsck on it from command line, and an error message says the superblock is corrupted.  I think I may be hosed.

---

### Post by windfix on 2008-10-04
*I recovered my few important files using "gksudo nautilus" from the terminal.  This is an awesome strategy, giving you root privilege in the GUI file browser. (booting from CD, you don't have permissions to copy your existing files anymore.)  Need to use Properties | Permissions | on each file and change to 'Read & Write'.  Then copied them off to a USB thumbdrive.*

Still - my partition won't boot.  Ready to reinstall, I tried the partition editor one last time.  This time, it completed successfully in minutes - AND fixed the original problem of misreporting the available space.

BUT - I still can't boot.

---

### Post by windfix on 2008-10-09
I finally just reinstalled and moved up to Intrepid, 8.10.  Running smoothly now.

---

