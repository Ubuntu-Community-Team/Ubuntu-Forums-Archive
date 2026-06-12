---
title: "Various Transfer speed problem"
date: 2006-12-17
forum: Hardware &amp; Laptops
---

### Post by Roguespider13 on 2006-12-17
I've been having a problem for a bit now and I've searched online but everything hasn't worked.

System Specs:
Unbuntu Dapper Drake 6.06
Dell GX260
P4 2.4 GHz
768 MB PC2100(might be 2700) DDR RAM
Devices: 
Primary: 20GB (root), 400GB(hdb)
Secondary: DVD drive, 400GB(hdd)

all 3 HDDs are using UDMA5.
Samba server running with 3 main shares: 1st on hdb, which is all of its data. 2nd and 3rd on hdd and both together are all the data on hdd. 


when I try copying any data (from either hdd or DVD) to hdb or hdd,  through GNOME or terminal it takes forever (appr. 10-15 minutes for a 150 MB file). Copy data from either drive to hda is fast (appr. 6 seconds). It seems that writes to the drive take a long time. 

What makes the problem in weirder is that I can copy the data from a Windows machine through the Samba server faster. The same 150 MB file will take appr. 3 minutes.

I would appreciate any help on this as I would like to be able to copy files natively rather than having to use a Windows machine as a middle man. If there is anymore data you need about my machine let me know, though be warned I'm a near newb with Ubuntu and Linux in general.

-Rogue

---

