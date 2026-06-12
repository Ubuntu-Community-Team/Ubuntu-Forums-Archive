---
title: "ARCHOS key"
date: 2011-01-21
forum: Hardware
---

### Post by fouvolant on 2011-01-21
Hi,

I have an ARCHOS Key:
[http://www.zone-numerique.com/news_6869_Key_le_baladeur_MP3_4_Go_a_l_ancienne_signe_Archos.htm](http://www.zone-numerique.com/news_6869_Key_le_baladeur_MP3_4_Go_a_l_ancienne_signe_Archos.htm)

I don't know why, but I cannot copy anymore file on it, it's on read-only!

--
paulo@paulo-desktop:/media$ sudo chmod 777 'ARCHOS Key'
[sudo] password for paulo: 
chmod: modification des permissions de «ARCHOS Key»: Système de fichiers accessible en lecture seulement
paulo@paulo-desktop:/media$ 
--
paulo@paulo-desktop:/media$ ls -l
total 24
drwx------ 6 paulo paulo 16384 1969-12-31 19:00 ARCHOS Key
lrwxrwxrwx 1 root  root      6 2009-10-09 03:08 cdrom -> cdrom0
drwxr-xr-x 2 root  root   4096 2009-10-09 03:08 cdrom0
lrwxrwxrwx 1 root  root      7 2009-10-09 03:08 floppy -> floppy0
drwxr-xr-x 2 root  root   4096 2009-10-09 03:08 floppy0

--
paulo@paulo-desktop:/media$ ls -l 'ARCHOS Key'
total 115568
drwx------ 4 paulo paulo    16384 2011-01-21 17:24 Carlos Libedinsky - Narcotango 2 [FLAC]  + covers
drwx------ 2 paulo paulo    16384 2004-01-03 19:56 FMIN.DIR
drwx------ 2 paulo paulo    16384 2004-01-03 19:56 MICIN.DIR
-rwxr-xr-x 1 paulo paulo 19786997 2011-01-17 14:52 Par 4 chemins - La santé et la conna 2.mp3
-rwxr-xr-x 1 paulo paulo 32605956 2010-10-04 09:56 Par 4 chemins - La santé et la conna 37.mp3
-rwxr-xr-x 1 paulo paulo 36538365 2011-01-17 14:53 Par 4 chemins - La santé et la conna 3.mp3
-rwxr-xr-x 1 paulo paulo 29318188 2011-01-17 14:53 Par 4 chemins - La santé et la conna 4.mp3
--

What should I do to put it back to read/write mode?

Thanks for your help.

---

