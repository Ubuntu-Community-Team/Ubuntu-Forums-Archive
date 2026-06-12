---
title: "Converting NTFS to ext3"
date: 2006-08-03
forum: Hardware &amp; Laptops
---

### Post by Princey on 2006-08-03
[FONT="Comic Sans MS"][SIZE="3"]Hi. I know there's a similar but outdated [thread]("http://www.ubuntuforums.org/showthread.php?t=50170&highlight=Converting+NTFS+ext3") that asks the question but I want to take this a bit further in asking here. I dual boot with Windows and I'm going full time Linux now except when I feel the need to play FIFA 2006. That means all of my programs will run under linux. I run a FTP server on my network and share with the neighbours. I know the disk type, ntfs or ext3 or reiserfs doesn't matter as to which is run, however, I want to be able to save from within linux on that partition that the ftp server is run from. Seeing it's on the same machine that I use, I'm thinking of converting to ext3. I've done an extensive search but can't find a simple way of converting to ext3 without data loss. Is that really possible? If not, is there a simple way I can mount that ntfs, copy and compress to a folder, reformat that drive and copy the data back without going the long manual way? Any heads up will be appreciated.[/SIZE][/FONT]

---

### Post by kaffelars on 2006-08-03
I'm *pretty sure* you can not convert NTFS to EXT3, you'd have to reformat the drive (just remember backup :wink: )

The write support for NTFS hasn't been that well as far as I know, but just a few days ago I think that changed. However, I don't now how to install that new driver in Linux.

---

### Post by mozetti on 2006-08-03
From some basic searching, it looks like there isn't a way to convert NTFS to ext2/3 or even NTFS->FAT32->ext2/3.

You could, however, convert NTFS to FAT32.

---

### Post by Princey on 2006-08-03
> **mozetti said:**
> From some basic searching, it looks like there isn't a way to convert NTFS to ext2/3 or even NTFS->FAT32->ext2/3.

You could, however, convert NTFS to FAT32.

[FONT="Comic Sans MS"][SIZE="3"]Thanks for the replies guys, but changing to FAT32 is out of the question because of the file limits. At times we share movies on our network and FAT32 cannot save a file above 2GB. I can back up the files under linux but I once had problems with corrupted files doing that. That's why is there a relative simple way to do it like zipping the files and copying them to my home directory, format the ntfs drive to ext3 and copy back over? As for NTFS write support, from what I've been reading and I could be wrong, there are still some limits as to what can or cannot be done especially writing aspect.[/SIZE][/FONT]

---

### Post by kaffelars on 2006-08-03
It is **not** possible to convert from NTFS to FAT32. (Only from FAT32 to NTFS if you don't want to reformat).

I'd back up the disk and then format it to whatever you find best for your needs. :)

---

