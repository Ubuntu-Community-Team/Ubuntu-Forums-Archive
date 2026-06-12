---
title: "Yay, new prolem."
date: 2006-02-02
forum: Installation &amp; Upgrades
---

### Post by solus.ipse on 2006-02-02
Ok I swear this HAS to be simple. 

First off I was able to bypass my installation restarting problems with "linux apci=off". 

So the problem at hand. XP has already set up at partion for my recovery files. 5 gb for a 200k file :-| Obviously I want to get rid of that partion but i'm getting scared when I read things like the entire disk will be formatted. Any ideas on how to "un-partion" my main drive with XP and dual boot with Ubuntu?

---

### Post by Adrian on 2006-02-02
[QUOTE=solus.ipse]
So the problem at hand. XP has already set up at partion for my recovery files. 5 gb for a 200k file :-| Obviously I want to get rid of that partion but i'm getting scared when I read things like the entire disk will be formatted. Any ideas on how to "un-partion" my main drive with XP and dual boot with Ubuntu?[/QUOTE]

Well, formatting your entire disk is not a good idea if you want to keep the windows partition :)

I recommend reading this guide about dual booting:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

When you get a feel for how the partitioner works, deleting that recovery partition should not be difficult (it is just a matter of selecting it and choosing "Delete partition").

---

### Post by solus.ipse on 2006-02-02
Well I just got the scare of my life. I decided to go with using bootitng which has a very nice partitioner. Upon deleting the partition and restarting I got an error the windows was unable to read my disk and could not start. Thank god I was able to "undelete" it. 

I have a 40 GB NTFS hd. 32.1 GB (with 12.8 free space) and a  5.13 GB partition. Can I make a partition with the 12 GB of free space? And how would I do that.

---

### Post by Adrian on 2006-02-02
[QUOTE=solus.ipse]Well I just got the scare of my life. I decided to go with using bootitng which has a very nice partitioner. Upon deleting the partition and restarting I got an error the windows was unable to read my disk and could not start. Thank god I was able to "undelete" it. [/QUOTE]
I guess you'd better leave it there for now then :)
You can try again (using some other method) when you really need that extra space.

> 
I have a 40 GB NTFS hd. 32.1 GB (with 12.8 free space) and a  5.13 GB partition. Can I make a partition with the 12 GB of free space? And how would I do that.

Yes, you can. Did you check out the guide I posted?
You need to resize your NTFS partition. Here is the section you want to read:
[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

Note that an alternative to creating an extra FAT32 partition for shared data, is to use this driver in Windows:
[http://www.fs-driver.org/](http://www.fs-driver.org/)
(to make Windows access ext2/ext3 partitions).

---

### Post by solus.ipse on 2006-02-02
I keep getting the same "size too small" error when choosing my partition. Out of curiosity I entered everything from the min to max and continued to get the same thing.

---

### Post by Adrian on 2006-02-02
[QUOTE=solus.ipse]I keep getting the same "size too small" error when choosing my partition. Out of curiosity I entered everything from the min to max and continued to get the same thing.[/QUOTE]

Did you resize your Windows partition, as described in the document?
Even though you don't utlize the entire partition, the partitioner will not be able to use that space unless you shrink it manually. (Note that shrinking a NTFS partition CAN cause data loss, so make sure to backup important data before trying).

How much free space did the paritioner report?

---

