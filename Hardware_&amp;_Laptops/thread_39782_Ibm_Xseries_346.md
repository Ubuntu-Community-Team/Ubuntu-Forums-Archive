---
title: "Ibm Xseries 346"
date: 2005-06-06
forum: Hardware &amp; Laptops
---

### Post by jlbarrera on 2005-06-06
Hello!
There is any problem in install Ubuntu Hoary 5.04 in IBM xSeries 346?
I want mount RAID 5 here.

XSERIES 346 REF. X02AGSP
DISCOS REF 30R5095
RAID REF 71P8642
MEMORIA REF 73P2866

Where i can find information of compatibility? It&#347; very important for my because the next week i have a installation for work questions.

sorry my English is ... :-? 

Thank you!

---

### Post by GrumpySmurf on 2005-06-06
The best place to find information about IBM hardware is [http://www.ibm.com/](http://www.ibm.com/).  Currently IBM 'officially supports' a few select distributions, like Red Hat and SuSE Enterprise.  

You can certainly install Ubuntu on your X346, but you might not get any Linux-related support from IBM.  I recently saw a link to a "compatibility list" for Linux distributions and various hardware platforms on the IBM site but I can't find the bookmark right now.

As for RAID5... most xSeries systems come with ServeRAID adapters that will support hardware RAID5 arrays.  This is recommended over a software array on any OS, I believe.  The array will be seen under Linux (any distribution) as a SCSI disk, usually /dev/sda.  Ubuntu can be installed here just as any other distribution.

---

### Post by Knightwise on 2008-06-11
Hey Guys, 

Has anyone found a solution to this problem ? Cause I have A ibm 346 server here with 2 140 gig drives in raid one (mirror) using the adaptec hostbios. When I try to install hardy server it sees 2 drives (where it should only see ONE drive) so the raid adapter does not seem to be supported. Has anybody had this problem or found a solution ?

---

