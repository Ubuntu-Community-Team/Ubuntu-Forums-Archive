---
title: "Lost storage on external harddrive"
date: 2012-08-04
forum: Hardware
---

### Post by Sekundarliterat on 2012-08-04
I've bought a 2TB external harddrive as a backup drive. The actual storage capacity is around 1.8TB, but after I tried to delete 400GB, this storage isn't accessible anymore. So I have 1.4TB left. 
This is, because I was impatient with the trash and I aborted the deleting process after 10 min. 
The harddrive is a La-Cie, the system in use is gnome ubuntu x64, if that matters. 

I've read about a program named scandisk, but it seems that only works on XP/Win. Is there a program working on ubuntu to repair errors on harddrives?

---

### Post by Nutria on 2012-08-04
> **Sekundarliterat said:**
> I've bought a 2TB external harddrive as a backup drive. The actual storage capacity is around 1.8TB, but after I tried to delete 400GB, this storage isn't accessible anymore. So I have 1.4TB left. 
This is, because I was impatient with the trash and I aborted the deleting process after 10 min.

Have you looked in the Trash?

Did you eject it safely? 

> I've read about a program named scandisk, but it seems that only works on XP/Win. Is there a program working on ubuntu to repair errors on harddrives?

```
fsck
``` is the closest Linux equivalent.

---

### Post by ranger1021994 on 2012-08-04
See if there is .Trash1000 file on your external
If it is present then delete the 'Files' folder from it

---

### Post by Sekundarliterat on 2012-08-04
There is no .Trash1000 file on the harddrive. 

The harddrvie type is NTFS. 

A save removal was after I terminated the process without an error  report not possible. I've checked and "repaired" the external with a  Win7, but there is no change in the volume capacity. Defragmentation  also didn't work. 

I tried the option "check and repair" with the advised program "fsck", but there is an error report: 

[[IMG]http://www7.pic-upload.de/04.08.12/zkdwmhofbxd.png[/IMG]]("http://www.pic-upload.de/view-15445959/fehlermeldung_fsck_LA_CIE.png.html")

---

### Post by Nutria on 2012-08-04
> **Sekundarliterat said:**
> The harddrvie type is NTFS.

You'd have saved everyone so much time and wasted effort by being *complete* in your OP.

Now you need to go to Google to search for missing capacity in NTFS partitions.

---

