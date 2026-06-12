---
title: "Which filesystem for /home ?"
date: 2008-10-08
forum: General Help
---

### Post by armageddon08 on 2008-10-08
I am reinstalling Ubuntu(dual-booting with Windows XP). I'd like to share my /home partition to be shared between both Ubuntu and XP(read/write access for both the OS). So which FS should I use(ext3/NTFS/FAT32)?

---

### Post by justleen on 2008-10-08
I'd say ext3, and install the ext-driver for windows..

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by armageddon08 on 2008-10-08
> **justleen said:**
> I'd say ext3, and install the ext-driver for windows..

[http://www.fs-driver.org/](http://www.fs-driver.org/)

Is it gonna work cool? I mean, no flaws/no data-loss etc?
Also, I've an 80 gigs HD. I'd be using Windows for gaming(mostly). So, could you guys give me a good partitioning outline?

---

### Post by justleen on 2008-10-08
Yup, works flawlessly (so far anyway).. i even install games from windows onto a ext3 partition, that works without probs..

i'd say for the partitions:
20gb xp  ntfs
10gb /home ext3
50gb /

(you can split / more offcourse... )
/boot  50mb
/etc   100mb
/var   > 1gb
/usr   > 4gb
/lib   > 1gb
/      > 500mb

something like that..

---

### Post by geirha on 2008-10-08
> **justleen said:**
> 
i'd say for the partitions:
20gb xp  ntfs
10gb /home ext3
50gb /


I'm betting justleen meant to write 50GB /home and 10GB / ? :)

---

### Post by armageddon08 on 2008-10-08
> **justleen said:**
> Yup, works flawlessly (so far anyway).. i even install games from windows onto a ext3 partition, that works without probs..

i'd say for the partitions:
20gb xp  ntfs
10gb /home ext3
50gb /

(you can split / more offcourse... )
/boot  50mb
/etc   100mb
/var   > 1gb
/usr   > 4gb
/lib   > 1gb
/      > 500mb

something like that..
Is it necessary to give so much space to /. i'd like to give max. space to /home.

---

### Post by airtonix on 2008-10-08
> and install the ext-driver for windows..Good luck with that....just dont create any symlinks....windows implementation of ext3 access is subpar and i wouldn't trust it in a fit.

if you want to use files from both sides. i recommend you just make a large fat32 partition...its the safest way.

Ideal setup for just about anyone : 
```

1.  1gb  -> /swap  swapfs
2. 10gb  -> /      ext3
3.  ~gb  -> /home  ext3

```

---

### Post by geirha on 2008-10-08
I haven't tried the ext driver for windows myself, so if it doesn't handle symlinks as airtonix mentions, I'd say go for fat32 as well. Though, don't use fat32 for /home ... Either mount it at /media/share or something, or mount it under your homedir somewhere. /home/yourusername/share.

---

### Post by armageddon08 on 2008-10-08
> **geirha said:**
> I haven't tried the ext driver for windows myself, so if it doesn't handle symlinks as airtonix mentions, I'd say go for fat32 as well. Though, don't use fat32 for /home ... Either mount it at /media/share or something, or mount it under your homedir somewhere. /home/yourusername/share.

What's the catch with using FAT32 for /home directly?

---

### Post by vanadium on 2008-10-08
You should not use a file system that does not support Linux permissions for /home. Have the /home and the users home directories on an ext3 partition, and just have your user data (documents, pictures, etc.) on an ntfs or fat partition. You can create a convenient symbolic link to these data in your home directory, such that you can easily access your data as if it were on the same partition.

If you have windows XP, there is no reason to use fat32. Use ntfs, which Linux can read and write.

For a dual boot, I would just have a single Linux partition that is quite limited (10 GB at most, enough to hold system, applications and user configuration data). I would keep all the rest on the Windows partition and link to that whenever needed. Fortunately, I have a single boot system.

---

### Post by geirha on 2008-10-08
> **armageddon08 said:**
> What's the catch with using FAT32 for /home directly?

FAT32 doesn't handle permissions and symlinks, and a lot of programs won't like that, and some won't work at all because they require certain files to have a certain permission.

If you save documents to the ~/Documents/ folder, I think it's better to just move that folder to the fat32 drive, and put a symlink in its place. E.g.
```
mv ~/Documents /media/share/Documents
ln -s /media/share/Documents ~/Documents

```

If you save something to the default place for documents after that, they will end up in the documents folder on the fat32 filesystem. 

I'm just guessing here on what would be a useful setup for you.

---

### Post by armageddon08 on 2008-10-08
Thanks....guys for the help. I feel that, I now have enough information to start my reinstallation processes.

---

### Post by justleen on 2008-10-08
i really dont understand the negative reaction for the ext3 driver for XP.. as stated above, I do quite a lot of stuff from windows on an ext3 drive, and I havent encountered any problems.. symlinks dont work, true, but neither do they cause problems or give errors..

And yes, ntfs is an option to, since the ntfs-3g driver for linux works like a charm too. 
BUt since Im working 99% of the time on linux, i preffer ext3 over ntfs. But thats personal..

---

### Post by armageddon08 on 2008-10-09
> **justleen said:**
> i really dont understand the negative reaction for the ext3 driver for XP.. as stated above, I do quite a lot of stuff from windows on an ext3 drive, and I havent encountered any problems.. symlinks dont work, true, but neither do they cause problems or give errors..

And yes, ntfs is an option to, since the ntfs-3g driver for linux works like a charm too. 
BUt since Im working 99% of the time on linux, i preffer ext3 over ntfs. But thats personal..
While using the ext2ifs driver, could any kind of virus/malware affect the ext3 partition from Windows. Also, can I install Windows apps and games on the ext3 partition and run them from Windows flawlessly(no effect on performance etc.) ?

I'm also adding a poll to know which is the most popular method.

---

