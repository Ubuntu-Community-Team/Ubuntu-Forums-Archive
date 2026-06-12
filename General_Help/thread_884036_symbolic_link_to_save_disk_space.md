---
title: "symbolic link to save disk space"
date: 2008-08-08
forum: General Help
---

### Post by equity on 2008-08-08
My Linux partition is running low on memory, so I want to set some kind of symbolic link to my NTFS-partition in order to be able to save data in my home directory without charging its partition anymore.
I only tried "ln -s <source> <destination>" but this does not solve my problem.

Any help is appreciated, thanks in advance.

---

### Post by thirddeep on 2008-08-08
I think what you mean is that your Linux partition is running low on space :-)

To use your NTFS partition from your Windows machine you will need to create a new entry in /etc/fstab.

Something like :
```
//server/share    /mnt/dir   smbfs   username=user,password=xxx  0 0
```

---

### Post by unutbu on 2008-08-08
Suppose you have directories in your home account:

music
bin
images
doc

Make the same directories on your NTFS partition. Let's say the NTFS partition is mounted at /media/data.  Copy over all the files that are currently in ~/music into /media/data/music. (Same for bin, images, doc, etc). Now remove the empty directories ~/music, ~/bin, ~/images, ~/doc. 

Then type
```

ln -s /media/data/music ~/music 
ln -s /media/data/bin ~/bin 
ln -s /media/data/images ~/images 
ln -s /media/data/doc ~/doc 
```

Now whenever you add a file to ~/music, it will be deposited in /media/data/music.
(And similarly for bin, images, doc).

---

### Post by thirddeep on 2008-08-08
I perhaps wrongly assumed your NTFS partition is on a Windows machine.  If it's not, then the above comments with ln -s will work.

Thd.

---

### Post by Sycron on 2008-08-08
This works wonderfull on my eeepc :D.

---

### Post by equity on 2008-08-08
> **thirddeep said:**
> I perhaps wrongly assumed your NTFS partition is on a Windows machine.  If it's not, then the above comments with ln -s will work.

Thd.

Actually yes, there is no Windows on there. I just formatted the partition to ntfs because I got trouble with ext3 partitions considering privileges.
Btw what means "Thd"?




> 
Suppose you have directories in your home account:

music
bin
images
doc

Make the same directories on your NTFS partition. Let's say the NTFS partition is mounted at /media/data. Copy over all the files that are currently in ~/music into /media/data/music. (Same for bin, images, doc, etc). Now remove the empty directories ~/music, ~/bin, ~/images, ~/doc. 

Then type
Code:
ln -s /media/data/music ~/music 
ln -s /media/data/bin ~/bin 
ln -s /media/data/images ~/images 
ln -s /media/data/doc ~/doc
Now whenever you add a file to ~/music, it will be deposited in /media/data/music.
(And similarly for bin, images, doc).


Unfortunately this does not work.

---

### Post by equity on 2008-08-08
Sry, my fault! It works like a charme! Did not read hard enough initially  ;)

---

