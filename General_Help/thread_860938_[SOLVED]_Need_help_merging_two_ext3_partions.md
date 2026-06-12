---
title: "[SOLVED] Need help merging two ext3 partions"
date: 2008-07-16
forum: General Help
---

### Post by Walter Melon on 2008-07-16
I recently deleted my windows partition and am now running fully off of Ubuntu.  After I deleted it, I formatted the unallocated space to ext3.  So I have the one ext3 partition that Ubuntu is on.  The other is completely empty. I tried to resize it in gparted but it wouldn't work.  Here is the list of the partions: There's two swap partitions because I wanted to add more to swap so I thought that if I made two I could delete one of them and it would use the other one. Is there a program that would allow me to merge the two existing ext3 partitions into one?
 
/dev/sda2 - linux swap
/dev/sda3 - ext3 (where ubuntu is)
/dev/sda1 - ext3 (empty)
/dev/sda4 - linux swap

Thanks in advance

---

### Post by dcstar on 2008-07-16
> **Walter Melon said:**
> 
.......
 Is there a program that would allow me to merge the two existing ext3 partitions into one?
 
/dev/sda2 - linux swap
/dev/sda3 - ext3 (where ubuntu is)
/dev/sda1 - ext3 (empty)
/dev/sda4 - linux swap


You cannot "merge" any partitions. You can copy data from one partition of another or increase a partition's size into adjacent free space.

You create free space by deleting partitions.

---

### Post by Dutch70 on 2008-07-16
> **dcstar said:**
> You cannot "merge" any partitions. You can copy data from one partition of another or increase a partition's size into adjacent free space.

You create free space by deleting partitions.

+1 
 You need to delete /dev/sda1 agian, and then grow /dev/sda3, I'm quite sure you can only grow it from the left to the right though. 

Try and post a pic of your partitions to get more help.:)

---

### Post by Walter Melon on 2008-07-16
> **Dutch70 said:**
> +1 
Try and post a pic of your partitions to get more help.:)

heres the screenshot, hope it helps

[IMG]http://img522.imageshack.us/img522/6070/screenshotdevsdagpartedkl2.png[/IMG]

Thanks again

---

### Post by Dutch70 on 2008-07-16
Ok, first of all you said /sda1 was empty gparted says you're using 558.14 MiB. so I am going to treat it as if it were empty.

You need to delete /sda1 and do not format it.(you cant grow it if it is formatted) I would suggest you grow /sda3 since it is almost full. Some say 10 GiB and some say 20GiB, so I made mine 15GiB. And then keep it(sda3) as your / (root) partition, and then format the rest of /sda1 to ext3 and use it for /home. that would be similiar to merging them as you had previously asked.

check out this link on planning partitions...
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Dutch

---

### Post by Walter Melon on 2008-07-16
> **Dutch70 said:**
> Ok, first of all you said /sda1 was empty gparted says you're using 558.14 MiB. so I am going to treat it as if it were empty. 



I don't know why it says that when it actually was empty before I shut down my laptop.  Anyway, I'll do what you said and the link that you gave me was very helpful, too.  Thanks for all of your help.

---

### Post by Dutch70 on 2008-07-17
Glad to hear it, and you're welcome. 

It wasn't long ago that someone gave me that link, part of ubuntus' philosophy is "pay it forward" thats one reason I love it.

Dutch

---

### Post by rbmorse on 2008-07-17
> **Walter Melon said:**
> I don't know why it says that when it actually was empty before I shut down my laptop.  Anyway, I'll do what you said and the link that you gave me was very helpful, too.  Thanks for all of your help.

It says that because even though there is no user data in the partition, the file system uses some space for internal housekeeping (journals and the like). Most file manglers account for or don't display that usage, but parted doesn't know what those blocks on the partition are used for, it just knows they are there.

---

