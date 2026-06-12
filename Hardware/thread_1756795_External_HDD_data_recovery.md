---
title: "External HDD data recovery"
date: 2011-05-12
forum: Hardware
---

### Post by Oats1337 on 2011-05-12
Hello
I was attempting to clone my laptop HDD onto my WD Elements external using

dd if=/dev/sd1 of=/dev/sd2

and ignored the warnings that it could erase all of your data. Well it did and when everything was finished all 700g's were gone.

I haven't written or deleted any data onto the drive since then and about a week before this happened I used bleachbit to remove all "deleted" data.

Are there any (free) programs that could recover this data? I just need to be pointed into the right direction, thanks

---

### Post by oldfred on 2011-05-12
dd stands for Data Destroyer.

Your command does not look correct. Was it sdd1 to sdd2? and what were the sizes of the partitions. 

Since dd copies every bit - bit by bit it will even write the zeros. Only if the to location was larger than the from may you even have any data left.

Testdisk/photorec is the tool to use to see what is there, but I would not get my hopes up.

Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
How to recover lost files after you accidentally wipe your hard drive
[http://www.linux.com/archive/feed/56588](http://www.linux.com/archive/feed/56588)
gddrescue, Scalpel, magic rescue, photorec, foremost, sleuthkit & others
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
How to recover lost files after you accidentally wipe your hard drive
[http://www.linux.com/archive/feed/56588](http://www.linux.com/archive/feed/56588)

---

### Post by jerrrys on 2011-05-12
testdisd is a good product.  in the future may want to give [clonezilla]("http://clonezilla.org/") a try

---

### Post by Oats1337 on 2011-05-16
Thanks fo rthe help Ill try out these programs
I got nothing when I used TeskDisk right after it happened

---

### Post by camronjack on 2011-05-17
First you have to ascertain that you have just wiped your data or after wiping the free space, is it zero filled and if that so for the matter of the fact overwritten data can not be recovered

---

