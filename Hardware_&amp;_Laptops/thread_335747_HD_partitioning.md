---
title: "HD partitioning"
date: 2007-01-10
forum: Hardware &amp; Laptops
---

### Post by nihalz on 2007-01-10
hi 
i just installed ubuntu edgy on my laptop and i must say its an awesome os...
i have a 80 GB hard drive....and its partitioned according to the image below...
[IMG]http://i18.tinypic.com/2ztas03.png[/IMG]
as you can see i have ubuntu installed and an ntfs partition which has xp professional...
there is 54gb of unallocated space left....and i want to make a new FAT32 partition from it so that it can be accessed both from ubuntu and xp...
my question is, do i make a primary partition or an extended partition from the unallocated space???i only get the option for primary or extended..
any help would be appreciated
thanks

---

### Post by taurus on 2007-01-10
If you don't plan to resize your harddrive anymore, then make it a primary but remember, you can only have four primary partitions but you can have many logical partitions under an extended partition.  Therefore, you can make it as an extended partition and create a logical with that empty space.  Either way is good.

---

