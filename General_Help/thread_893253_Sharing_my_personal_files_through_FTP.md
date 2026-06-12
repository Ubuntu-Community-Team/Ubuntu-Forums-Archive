---
title: "Sharing my personal files through FTP"
date: 2008-08-18
forum: General Help
---

### Post by TheOrangePeanut on 2008-08-18
I'm trying to set up an FTP server so my roommates can get my files when they need them.  This is all going to be on my local network.  I installed vsftpd and it made the /home/ftp directory, so I made symlinks to two folders on my computer under that directory.  This didn't work as I had hoped, though; when I try to access them through an FTP client I get a "cannot change directory" error.

Is there a way to link my files to my ftp directory without actually moving them there?

---

### Post by mikjp on 2008-08-18
I think that is a security feature of vsftpd (very secure ftp daemon) that limits the ftp user to a specific directory.

You might try to use a less secure ftp daemon :-)

mikko

---

