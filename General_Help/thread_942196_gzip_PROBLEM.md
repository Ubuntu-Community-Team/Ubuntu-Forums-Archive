---
title: "gzip PROBLEM"
date: 2008-10-08
forum: General Help
---

### Post by harakiri1976 on 2008-10-08
Hello to all!

I have a problem. I pretend to backup 70 GB of Data from a 150GB FAT32 Partition. I tried to compress the Data in a *.tar.gz archive. I used gzip to compress it. But the problem is that gzip limits the *.tar.gz archive to 4GB. See below...

1st - Tried to backup ALL files in /media/Dados/

```

tar backup_DATA.tar.gz /media/Dados/Filmes/ /media/Dados/Music/

```

```

/media/Dados/Filmes/
/media/Dados/Filmes/SpiderMan 3/
/media/Dados/Filmes/SpiderMan 3/CD 2/
/media/Dados/Filmes/SpiderMan 3/CD 2/p-s3-cd2.avi
/media/Dados/Filmes/SpiderMan 3/CD 1/
/media/Dados/Filmes/SpiderMan 3/CD 1/p-s3-cd1.avi
/media/Dados/Filmes/Piratas das Caraíbas/
/media/Dados/Filmes/Piratas das Caraíbas/pirates_of_the_caribbean_dead_man's_chest_part1_x264.mkv
/media/Dados/Filmes/Piratas das Caraíbas/pirates_of_the_caribbean_dead_man's_chest_part2_x264.mkv
/media/Dados/Filmes/Mr Brooks/
/media/Dados/Filmes/Mr Brooks/CD 2/
/media/Dados/Filmes/Mr Brooks/CD 2/Mr.Brooks.DVDRiP.XViD-HLSb.avi

gzip: stdout: File too large


``` 

How can I create a 70GB .tar.gz file to store in a USB External Hard-Drive?


BTW, "Dados" is Data in Portuguese

---

### Post by harakiri1976 on 2008-10-08
It's not very important for the case, but I forgot to post the "flags" in the tar command.

```

tar -cvpzf backup_DATA.tar.gz /media/Dados/Filmes /media/Dados/Music/

```

---

### Post by harakiri1976 on 2008-10-08
Well, as I can see it's not a GZIP problem, It's because the drive where the archive is being created is FAT32. And because of that, FAT32 filesystems has 4GB filesize limitation. Check this post below...

[http://ubuntuforums.org/showthread.php?t=163857](http://ubuntuforums.org/showthread.php?t=163857)

Now, I have to find a way to compress with .tar.gz and with a pipe split the archives in 3GB for instance

---

