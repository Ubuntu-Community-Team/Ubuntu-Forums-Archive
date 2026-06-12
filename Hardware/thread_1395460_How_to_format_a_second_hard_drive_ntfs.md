---
title: "How to format a second hard drive ntfs?"
date: 2010-01-31
forum: Hardware
---

### Post by bettyhills on 2010-01-31
I added a second 60gb hdd to my system that was formerly fat32 in its old life.  (It replaces a 10gb slave drive.)  I would like to format it ntfs before using it.  Can anyone tell me exactly how to do that, step by step (a beginner here)?

---

### Post by Bucky Ball on 2010-01-31
System->Administration->Partition Editor 

Choose the drive from the drop down box in the right hand top corner.

Right click on the free space you want to partition, 'Format to ...' and choose ntfs.

---

### Post by bettyhills on 2010-02-01
Thank you for the quick reply.  Partition Editor was not one of my options under Administration, however I installed gparted using Synaptic and it became available. 

When I follow your instructions, all works as you say except that ntfs as an option is grayed out.  The entire drive is available for partitioning.  It is currently a Fat32 drive with remnants of a Windows98 system on it.  Can I prepare it somehow to allow for ntfs?  

I noticed Partition Editor has an option to change the partition to a MS-DOS configuration but do not want to do anything that could be fatal without advice. 

OR do I delete the Fat32 Partition and then install it again as ntfs?

How to get the internal 60gb Fat32 slave drive formatted ntfs under Ubuntu?

Help needed.

---

### Post by Jason Raub on 2010-02-01
Hello, I'm a novice linux user but I know a little bit how Gparted work's. You unmount the drive in gparted first (if it's mounted) then you right click on the drive in gparted and use the delete option (this deletes all partitions not the drive itself) then find the drop down box (apply all changes) then when thats done right click on your blank drive and select "new" then from there you just select "ntfs" instead of the default "ext2" and apply changes from there. I'm telling you out of memory so I hope it help's at leist a little.

---

### Post by bettyhills on 2010-02-01
Thank you both, BB & Jason.  Partition Editor does not allow for unmounting.  Under Partition Editor, tried deleting the partition.  Then repartitioned but, again, ntfs as an option is grayed out so was forced to partition it as Fat32.

Can anyone instruct me step by step under gparted as to how to format the 60gb slave drive ntfs?

---

### Post by oldfred on 2010-02-01
Newer versions of Ubuntu now include the ntfs drivers as they are very stable. A couple of years ago they were just starting to become stable so they may not be included in your install and may not be in the standard liveCD.

Go into synaptic and download ntfs-3g. I would also download ntfsprogs in case you want to do minor maintenance, but windows is usually required for major maintenance.

---

### Post by bettyhills on 2010-02-01
The problem is SOLVED. For anyone else who might follow this thread later, all the instructions above are correct.  My Ubuntu installation was balking for some reason.  

However, [http://howtoforge.com/partitioning_with_gparted](http://howtoforge.com/partitioning_with_gparted) said to create a gparted live cd which I did.  Booting from the live CD, miraculously the instructions worked.  The slave 60gb drive is formatted ntfs.  

I will go snag ntfs-3g and ntfs-progs from Synaptic right now.

Thanks to all for your help!

---

### Post by Bucky Ball on 2010-02-01
Good news. Yep, should have said that the drive needs to be unmounted. LiveCD is the go but you can also unmount through a terminal. You can not, of course, unmount the partition that Ubuntu is actually running from so if you want to re-size that partition it HAS to be done with a LiveCD. 

Have fun ... :)

---

