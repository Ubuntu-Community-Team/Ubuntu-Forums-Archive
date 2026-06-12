---
title: "Having trouble mounting Western Digital My Book World Edition"
date: 2021-01-24
forum: Hardware
---

### Post by eddiemccullough on 2021-01-24
Hello everyone, I am very new to Ubuntu and everything linux.  I am very  much enjoying its simplicity.  I recently switched my laptop over to  Ubuntu 20.04, completely getting rid of the Windows 10.1 that was on  this laptop.  Our home recently had multiple power surges from a really  bad storm and our Western Digital My Book World Edition nic went out.   It no longer connects to the network.  With a little diggin around the  forum and the internet, I'm not sure if I know how to mount the HDD to  my laptop so I can retrieve our data.

Would anyone be willing to help?  I currently have the HDD removed, and  connected via a SATA to USB with a power supply.  I do know the hard  drive works because when I open up a terminal session and type $ sudo  fdisk -l I can see the drive and the partitions:

Disk /dev/sdb: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: EADS-11M2B2     
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000300

Device     Boot   Start        End    Sectors   Size Id Type
/dev/sdb1         64320    3984191    3919872   1.9G fd Linux raid autodetect
/dev/sdb2       3984192    4498175     513984   251M fd Linux raid autodetect
/dev/sdb3       4498176    6474175    1976000 964.9M fd Linux raid autodetect
/dev/sdb4       6474176 1953520064 1947045889 928.4G fd Linux raid autodetect

After this, I'm 100% positive I don't know what I'm doing.  I created a  new directory, and tried to mount it to that directory, but I get an  error.
$ sudo mkdir /media/mount
$ sudo mount -t ext3 /dev/sdb4 /media/mount
And I get this once I hit enter:
mount: /media/mount: /dev/sdb4 already mounted or mount point busy.

This is pretty much as far as I can go all on my own.  If someone could help me a bit, I sure would appreciate it very much.

---

### Post by CelticWarrior on 2021-01-25
Welcome.

I won't be able to help you but hopefully give a clue to what's happening and other experienced users may take it from here.
The issue seems to be the "Linux raid", typical of many NAS devices. It's not a simple matter of extracting and connecting the internal HDD. I'm not sure the correct RAID can be remounted in another machine but, again, the experienced user should take it from here.

---

### Post by eddiemccullough on 2021-01-25
Thank you for the welcome!

I had a feeling that the Linux raid has something to do with it.  My Wife and I are not that savvy when it comes to stuff like this.  I thought raid was only typical when there are for two drives, as in two independent HDD.  I guess you can setup raid when there are different partitions?

I think it can be done.  I have a lot of confidence in this forum, and I'm looking forward to learning.

---

### Post by eddiemccullough on 2021-01-25
I'm still doing some research on the problem of the drive not being mounted possibly due to raid, and I think I found something interesting on the 'net.  I found another forum where a user said that you need to remove the raid in order for it to be mounted.

In the terminal you need to be a super user (I actually know how to do that).
Get gparted software (apt install gparted) and to also get mdadm,
Run to see partion, remove Raid flag.

Does any of this sound like it would be correct?

After a little digging, my NAS does have Raid even though its one drive, and the file system is XFL so when I mount it, I need to make sure when I mount it has the correct fs.  In my first first post I was trying to mount it using ext3.

---

### Post by CelticWarrior on 2021-01-25
Yes, that you need to remove the raid flag sounds familiar. That will probably make any data recovery impossible.
If you just want to reuse the drive and don't care about files that may still be there then with Gparted > Device menu > Create new partition table... should be enough.

---

### Post by eddiemccullough on 2021-01-25
I ran gparted, and I can still see the HDD that came out of the Western Digital NAS.  I also see all of the partitions on there. The partition /dev/sdb4 no longer has raid, I right clicked on the partition and went to manage flags, unchecked raid and then hit close.  Gparted ran another scan, and I can confirm that raid has been removed from that partition.

When I went to mount dev/sdb4, its still giving me that error "already mounted".  Crazy.

In gparted, under the dev/sdb4 partition, it does say that the mount point is /dev/md2.  Not sure what that means....

---

### Post by eddiemccullough on 2021-01-25
Solved
XFS Data Recovery by Reclaime works perfectly. It cost $200 for a license, but it doesn’t matter. Our first born pictures, second born, family events and videos are important enough to warrant $200 expense.

Thanks for the help! Seems like there wasn’t something quite right with my file system. I started going down the rabbit hole of the structure needing cleaning etc...reclaime literally makes it easy to access all the files exactly how I had them organized, including deleted files which I thought was pretty neat.

---

### Post by CelticWarrior on 2021-01-26
I'm glad you solved it.

Normally I wouldn't recommend commercial solutions and even strongly advocate against them but only you know the value of the data to be recovered.

---

