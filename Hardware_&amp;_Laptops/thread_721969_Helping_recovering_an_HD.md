---
title: "Helping recovering an HD"
date: 2008-03-11
forum: Hardware &amp; Laptops
---

### Post by pavallokazzo on 2008-03-11
Hi all.
A my HD is leavin me, with some problems.
I was passing to the new storage unit while found out that the old one is full of problems, so I'm trying to recover the data from it.
It's a 160GB unique reiserfs partition.
I've been able to transfer almost everything apart 18GB of data I would like to keep and seems it can't just cp.
Problem is I ain't got an HD that could contain an image of that partition' size as my biggest is 250 GB and actually is the replacement, already almost full of data...
I went out with the idea to fill the free data on the reiserfs partition with zeros 
# dd if=/dev/zero of=/mnt/reiserfs160gbhd/fill.zero
then remove it and do a light compressed image of the partition
# dd if=/mnt/reiserfs160gbhd/ of=- | tar something # i don't remember the command
then start trying to recover data directly in the reiser' hd, maybe with tree rebuilds or some option of that in the fsck command
(or perhaps doing a 
# dd if=/dev/zero of=/dev/hdreiser 
wishing that all the problems where just erroneus write and putting again the image on the hd...)
does the fill zero thing remove some possibility to restore the data?
again, all the data I could have be able to access is already safely stored so I need only to retrieve those 18gb...
another thing I went with is to try to reduce the size of the partition so the image can fit in another 160GB hd formatted in ext3... but I think this can causes more damage then anything else...
last option will be to move the data of the 250 GB hd in different hard drives but it will take huuuge time!
let me know
thx

EDIT: forgot to say that the device doesn't make any weird sounds at all, I've been transferring file all day while sitting on the computer at the side and didn't heard anything strange... strange!

---

### Post by pavallokazzo on 2008-03-12
bump!

---

