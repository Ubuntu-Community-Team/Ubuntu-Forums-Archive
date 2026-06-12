---
title: "Can't Mount HDD"
date: 2010-03-19
forum: Hardware
---

### Post by Jonny87 on 2010-03-19
I'm having trouble with accessing a brand new hard drive. I just put it in the computer and the start of the week, replacing one that failed. Its formatted in ext4 and was working perfectly fine then yesterday when I was trying to access it (hoping to be able to back up the data) it came up with an error that read.
 
> 
**Unable to mount Library**
 
Error mounting: mount exited with exit code 32: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
     missing codepage or helper program, or other error
     In some cases useful info is found in syslog - try
     dmesg | tail or so

 
Does anyone know what this means and is it still possible to some how get the files of it and back them up?

---

### Post by jrssystemsnet on 2010-03-19
> **Jonny87 said:**
> I'm having trouble with accessing a brand new hard drive. I just put it in the computer and the start of the week, replacing one that failed. Its formatted in ext4 and was working perfectly fine then yesterday when I was trying to access it (hoping to be able to back up the data) it came up with an error that read.
 

 
Does anyone know what this means and is it still possible to some how get the files of it and back them up? You can try fsck'ing the drive using an alternate superblock.  Google "fsck ext alternate superblock" and you should get a how-to pretty quickly.

If these files are really important and you have the resources, you should make an image of the drive onto another drive before you do this.  If you don't have the resources, don't worry about it, just do the fsck with the alternate superblock and hope for the best.

---

### Post by Jonny87 on 2010-03-19
I had thought about goasting it to backup the data. But was wondering would that copy the problem as well, leaving the image just as useless as the origanal?

---

### Post by jrssystemsnet on 2010-03-19
> **Jonny87 said:**
> I had thought about goasting it to backup the data. But was wondering would that copy the problem as well, leaving the image just as useless as the origanal?Well, yes.  But the point of making the image is to preserve the original problem, which could theoretically be more recoverable from than the problem AFTER you fsck it. :)

Of course, odds are, if fsck won't fix it you aren't ever going to fix it, which is why I said if you don't have the resources to make the image, don't sweat it, just go ahead and fsck it with the alternate superblock.

---

### Post by Jonny87 on 2010-03-21
Well I got it fixed by doing a file system check&fix. Didn't lose the data either. however while trying to ghost the drive I accidentally stuffed it up and wiped my back up drive by stupidly not thinking about what I was doing. Oh well, my own stupid fault I guess.

---

