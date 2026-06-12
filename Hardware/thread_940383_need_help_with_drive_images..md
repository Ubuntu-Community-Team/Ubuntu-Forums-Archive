---
title: "need help with drive images."
date: 2008-10-07
forum: Hardware
---

### Post by TheLocalGraveDigger on 2008-10-07
this probably does not belong in the Hardware & Laptops section but I'm not sure where to ask this.I am trying to shrink a pair of partitions using gparted then make an image of the two in a way i can place it back on a drive later. using the dd utility i can create a file but the file is the size of the disk that the partitions are on and that defeats the purpose of shrinking the partitions inside :(. I need a way of making the file end at the end of the last partition. The reason for this is i plan to put Ubuntu on a laptop that has vista on it. being an OEM copy i cant fix the install if things go bad. The second partition seems iffy to me as a recovery option and takes up space that i don't want taken on a laptop. I want a file that i can store somewhere else that i can use to repair vista myself so i don't have to deal with Future Shop for it. but I cant really afford to keep a 160 GB file or use a full 160 GB drive to substitute for an install CD. I would appreciate any help you can give me(and if you could put this post wherever it belongs because I'm not sure).

---

### Post by cariboo on 2008-10-07
You may want to give partimage a try, it doesn't duplicate the empty space on your disk like dd does. Partimage is available in the repositories.

Jim

---

### Post by jpkotta on 2008-10-07
You could compress the output of dd.  If they're mostly empty, disk images are very compressible.  gzip is fast, so the bottleneck will be the disk.

```
dd if=/dev/sdX | gzip > backup
```

I agree that there are better tools for the job than dd; it's pretty bare bones.

---

### Post by TheLocalGraveDigger on 2008-10-07
Iv downloaded partimage but it seems it only supports individual partitions and the MBR/partition table separately. how exactly does it work?

and i have tried to compress with gzip in the manor you suggested earlier today but i cant figure out how to reverse the process.

I do appreciate your quick replies but as its about 4 AM here I'm going to tackle this again in the morning.

---

### Post by TheLocalGraveDigger on 2008-10-08
OK i got this code here

# dd if=/dev/<laptop HDD> | gzip > /mnt/hda/Vista_Laptop_backup.img.gz
# gzip -dc /mnt/hda/Vista_Laptop_backup.img.gz | dd of=/dev/<laptop HDD>

Will this do what I'm asking? Because the situation has changed slightly. the laptops drive is now 320 GB but the software should not increase. I still need to fit the image on my 160 GB drive. Please respond with a confirmation or a correction before Friday night. Thanks for your help thus far :) .

---

### Post by TheLocalGraveDigger on 2008-10-08
P.S. i got that code from
[http://wiki.linuxquestions.org/wiki/Dd](http://wiki.linuxquestions.org/wiki/Dd)
Creating a hard drive backup image
But i need some verification first.

---

### Post by TheLocalGraveDigger on 2008-10-15
Worked like a charm:)... good thing too, as vista died after trying to resize some partitions and the recovery disks they gave me...were blank dvds that i needed to make myself:(

---

