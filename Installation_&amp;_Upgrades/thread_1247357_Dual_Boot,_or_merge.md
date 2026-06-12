---
title: "Dual Boot, or merge"
date: 2009-08-22
forum: Installation &amp; Upgrades
---

### Post by jakeford18 on 2009-08-22
Due to a lack of "terminal" understanding , I was unable to get my ethernet port working when I unwisely upgrade from 8.10 to 9.04. Luckily using a variety of Arconis Disk Management tools, I was able to back up 60 gigs of various media and move it to a logical paritiion. (I have a 250gb WD HD, splint into two paritions) Then after I deleted the primary partition containing 9.04, I was able to re-install 8.10 64 bit, and restore my files from the logical partition back to the primary partition. This was a very long process, it took about 2 hours to back up the data, another 36min to validate it, and 2 hours to restore it. Now that the logical parition is empty, I am wondering if I should A. use a combination Arconis Disk Mangagement Tools, to Run 8.10 64bit on one partition, and 8.10 I386, on the other. or B. just merge the two parititions, however I'm somewhat worried if I merge them, all my stuff will be lost, and this will have all been for nothing. I do have a version of Windows XP, but overall am much more satisfied with the Ubuntu Platform

---

### Post by zvacet on 2009-08-22
You can not merge primary and logical partition (AFAIK).Yes you can install 32 and 64 bit versions of same Ubuntu release but I don´t see point of doing that.Do you have separate home ( I believe you don´t)?If not make one following [this]("http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html") guide.You don´t need root bigger then 10-15GB so you can shrink your primary partition and use rest for home(except of swap of course).if you have any questions about this just ask.

---

### Post by jakeford18 on 2009-08-22
thanks for the advice, i just changed into another primary partition. problem solved.

---

