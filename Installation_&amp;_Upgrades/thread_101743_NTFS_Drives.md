---
title: "NTFS Drives"
date: 2005-12-10
forum: Installation &amp; Upgrades
---

### Post by Shimmerdark on 2005-12-10
I just switched my file server over from windows and have all the files on seperate drive in NTFS format. I mounted one and it is readable but I can't write to it for some reason or change permisions. Any idea why? I enabled root password to get this far. Please tell me that Ubuntu can read and write to NTFS drives.

---

### Post by audax321 on 2005-12-10
Unfortunately MS won't share the details of how to write to NTFS drives so you can't by default. There is experimental NTFS write support, but it will most likely corrupt the file system. The only format that has complete read/write support between Linux and Windows is FAT, but its not too great of a format.

Now, if you are just using FTP or SSH to transfer files, I would recommend trying a Linux file system. I used to run FAT32 on an FTP and after transferring files for years (without Windows to Defrag or ScanDisk), the file system went corrupt.

---

### Post by audax321 on 2005-12-10
Not sure if this will help but it has directions on how to write to NTFS. KEEP IN MIND, HOWEVER, THAT YOU COULD LOSE ALL YOUR DATA!!!!

Here's the link: [http://bisqwit.iki.fi/story/howto/ntfs/](http://bisqwit.iki.fi/story/howto/ntfs/)

---

### Post by dbeckham32 on 2005-12-10
I can not tell you how to write to a NTFS from Linux, however, you can use [http://www.fs-driver.org/](http://www.fs-driver.org/) to read and write to a Linux partition from Windows.

Sorry I could not be of more help.

---

