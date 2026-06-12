---
title: "problem with files permissions and FTP"
date: 2009-05-22
forum: Installation &amp; Upgrades
---

### Post by mirkko22 on 2009-05-22
Hi all

Is now 10 days I get some strange problem with FTP and files permissions....and I start to become totally crazy because I don't understand where is the issue...

For manage my files on my virtual server (running suphp) I have always use with great success Filezilla... All uploaded files/folder was always set immediately with attribute 644 for files and 755 for folder...and this is correct for my need...I never need to manually adjust permissions for any files because all stuff was always set with correct permissions 644 and 755...

Since 10 days now I don't know why when I upload files/folder all the stuff get 664 for files and 775 for folders.... I don't have change anything in Filezilla and I don't have update this software... I don't have also change nothing on my server...

I have try with some other FTP client (Kasablanca, Gftp, KftpGrabber and CuteFTP (available only for window but running with Wine) and I get same result...all stuff get attribute 664 and 775 when before attribute was set to 644 and 755...

I need to understand why now I get this problem when before everything was fine... I thinking it was a problem with Filezilla but after making some test with some other FTP client I see is not possible all client get a problem...so the only possibility are something go wrong with my server and files permissions... So I have contact my server provider and they make some test and check...but no problem with my server...it is well configured and all upload tests my provider do with same software was normal..all files permissions was correct...

I have finally test under Window using Filezilla and Cuteftp and I don't get any problem...My files are set with correct permissions...so now I am sure it is not a problem of my server or my ftp software...It appear to be a Ubuntu issue...but witch issue ????

I do always all update Ubuntu propose me almost every days...and it seem something was installed 10 days ago and make problem with FTP protocol...

Somebody have an idea ??? any suggestions ???

thanks

---

### Post by murrayim on 2009-05-23
Hi, 

 the second character belongs to the group owner... looks like you belong to that group and that group is picking up the same rights

hope this helps

[http://en.wikipedia.org/wiki/Chmod](http://en.wikipedia.org/wiki/Chmod)

---

### Post by mirkko22 on 2009-05-23
yes something like that....but why this happen now since 10 days ? Like I say I don't have made any special change...

Another thing very strange is if I try to upload files with another ftp client called IglooFTP I don't get any problem...and my files get correct attribute 644....What Iglooftp have in more for no make permissions problem ?

And why when I upload files under Window with any ftp client I don't get permissions problem ?

really don't understand.... :o((

---

