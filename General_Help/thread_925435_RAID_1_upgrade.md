---
title: "RAID 1 upgrade"
date: 2008-09-20
forum: General Help
---

### Post by R3N3G4D3 on 2008-09-20
I have my Ubuntu installed on a 80GB PATA drive. Recently I purchased 1.5TB SATA drive to use as storage. I plan to purchase a second one (1.5TB) in a couple of months to use in RAID 1 (the one that clones data) configuration with the one I just purchased. My question is, can I format the drive I just bought as a regular harddrive and start storing data on it now (cloning the data to 2nd drive later), or will I have to erase everything from it later to set up RAID 1 configuration? Also, my motherboard supports SATA RAID through Intel ICH7R chip, but it seems like their software is for use with Windows. Are there Linux alternatives for the software for this chip or will I have to run RAID completely through software? Thanks.

---

### Post by stickmangumby on 2008-09-20
Before I start, I'm not too familiar with the specifics of your problem. Hopefully I can provide some useful information though.

Most motherboards that have support for RAID don't actually have a dedicated RAID controller, so you have to use software to RAID you harddrives.

I very much doubt that you'll have to wipe your first drive in order to set up your RAID array.

Have a read about dmraid and mdadm for Linux software RAID.

The following link might provide you with some useful information as well:
[http://www.intel.com/support/chipsets/imsm/sb/CS-020663.htm](http://www.intel.com/support/chipsets/imsm/sb/CS-020663.htm)

---

### Post by fjgaude on 2008-09-20
Well, from my experience and knowledge for you to use one drive and put data on it, and then want to put that drive in a raid1 array, you will lose all the data on that drive. The reason being that after an array is created the filesystem is then added.

There are two ways with Linux to get to a raid array. If you use the onboard Intel raid setup then in Ubuntu you will have to use a program called **dmraid** to access the raid1 after booting.

If you wish you can create the raid1 array in Ubuntu using **mdadm**, which most of us do for raid0, 1, 5, 6, and 10. Both programs are on the repository for download and install.

Here's some stuff to read, study to get familiar with software raid:

[http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)
/usr/share/doc/mdadm/FAQ.gz and md.txt.gz
[http://blog.tcg.com/tcg/2006/04/recovering_raid.html](http://blog.tcg.com/tcg/2006/04/recovering_raid.html)
man dmraid
man mdadm

Let us know how you are doing.

---

### Post by phillik747 on 2008-10-03
I would love to do the same as R3N3G4D3. I have a server with a 750gb drive that I would like to setup as raid 1 later but I don't have the storage space, for all the data on the drive, to copy/backup before setting up raid.

I was wondering though, is there a way to virtually setup the raid with the missing second drive first? So then you can use the original hard drive as data storage and when you get the new drive you tell mdadm to rebuild/resync the data to the new drive?  Kind of like when you have a real failure and you just replace the bad drive with a new one. I would think this might be possible since /dev/md0 is somewhat of a virtual drive anyway.  (I'm a noob when it comes to raid. This is more of a brainstorm than anything)

I have 3 40gb bland hdd's to test with if someone has any ideas.

---

### Post by fjgaude on 2008-10-03
Well, I certainly don't know everything there is to know about **mdadm**, but to setup a raid, raid1 or whatever, you create the array then add the filesystem. If adding a filesystem doesn't destroy all the data on the one drive then I have learned something new.

It's easy to create an array with a "missing" drive or two, but the issue is the array has to have a filesystem added after its creation. That's my understanding presently.

---

### Post by phillik747 on 2008-10-03
Yes I'm sure that when you add the filesystem it will kill the data.  I will try creating a raid 1 setup with only one device to make /dev/md0.  And then add a second hdd and use ```
sudo mdadm --add /dev/md0 /dev/sdXX
```.

But first I have been playing around a bit with this.  

I started with a clean raid1 setup.  I then removed the second disk /dev/sdc1 and put in a unformated hdd (same size).  I then force stated /dev/md0 **Note I shutdown the pc when swapping hdd's**
```
sudo mdadm --run /dev/md0
``` 
and copied all the data I wanted to it. At this point I only have one disk in the raid1 setup.  Then I did the following to the clean new hdd:
```
sudo fdisk /dev/sdc

```
In fdisk I created the same partition table as sdb1 and changed the type to fd. I then created the filesystem on sdc1
```
sudo mkfs.ext3 /dev/sdc1
```

After the filesystem and partition table was the same as sdb1 I synced/rebuilt the data to rebuild the raid1 setup with two disks.
```
sudo mdadm --add /dev/md0 /dev/sdc1 && watch cat /proc/mdstat
```

This worked perfectly, I might have missed some commands but this is just a general thought process.

At this point on my home server with the 750GB HDD I do have the ability to format the disk and start from scratch but I wont be getting a second disk anytime soon.  (have to get the wife to approve the cost :D). So...that being said I hope I can create a 'fake' raid1 with only one disk one partition and later sync to a second disk. I will test this out and post my findings here.

Please let me know if I've fallen of my rocker. I just know enough to be dangerous!

---

### Post by fjgaude on 2008-10-03
What you are doing sounds like it works... so go for it... maybe after you do it again to make sure it truly does work.

Good luck!

---

### Post by phillik747 on 2008-10-08
Here is a link to the tutorial: [http://ubuntuforums.org/showthread.php?t=943155]("http://ubuntuforums.org/showthread.php?t=943155")

My testing worked! I'm going to write a tutorial on the process and post a link here once I get that done.

Basically I created a raid 1 device [/dev/md0] with one drive/partition and copied all the data to /dev/md0 that I wanted. When I wanted to add the second drive I just recreated /dev/md0 with the two matching drives/partitions and watched it sync up.  

So...to answer R3N3G4D3 question...YES, well kind of, but you have to set it up before you put your data on your first drive, then add the second drive later.

Again if there is anyone out there that more technical than I, I would love to send you the tutorial first for a proof read.

---

### Post by fjgaude on 2008-10-09
Questions: when you created md0 did you indicate a "missing" drive? What does it mean to "recreate" adding the second drive?

---

### Post by phillik747 on 2008-10-09
> **fjgaude said:**
> Questions: when you created md0 did you indicate a "missing" drive? What does it mean to "recreate" adding the second drive?

When you create /dev/md0 with just one drive you use:

```
sudo mdadm -C /dev/md0 -l 1 -f -n 1 /dev/sdb1
```

The -f is to force only using one drive (this defeats the purpose of raid 1 in the first place but allows you to get it setup when you don't have the equipment).

When you go to add the second drive you use:
```

sudo mdadm -C /dev/md0 -l 1 -n 2 /dev/sdb1 /dev/sdc1
```

You MUST put the drive with the data you want to keep first (sdb1). This tells mdadm to put the data on sdb1 to sdc1. Not to necessarily recreate but to copy/clone. I guess this is since sdb1 has a super-block of /dev/md0 while sdc1 does not.

I'm still working on my tutorial and will post a link in here when done. (the tutorial will be put in the Tutorials & Tips of ubuntuforums)

---

### Post by fjgaude on 2008-10-09
Thanks, I'm sure many will find what you have done useful... nothing in the man pages indicates you can do what you have found that can be done.

I'm looking forward to seeing what changes have occured in mdadm 2.6.7 that is shipped with 8.10, Intrepid.

---

### Post by phillik747 on 2008-10-10
Here is a link to the tutorial: [http://ubuntuforums.org/showthread.php?t=943155]("http://ubuntuforums.org/showthread.php?t=943155")

---

### Post by fjgaude on 2008-10-11
I read your tutorial. Clear and well done! It'll help many who go this route.

Also many try to use raid1 from which to boot... not so easy, but many have gotten it to work.

Software raid gets used more and more as the motherboards and CPU come up to speed. I feel that in a few years hardware raid will be dead to Linux.

Thanks again for taking the time to do it right! <smile>

---

### Post by phillik747 on 2008-10-12
> **fjgaude said:**
> I read your tutorial. Clear and well done! It'll help many who go this route.

Also many try to use raid1 from which to boot... not so easy, but many have gotten it to work.

Software raid gets used more and more as the motherboards and CPU come up to speed. I feel that in a few years hardware raid will be dead to Linux.

Thanks again for taking the time to do it right! <smile>

Thank you for the feedback.  I believe your right about software raid. There is something to be said about the ease of knowing your raid setup will work no matter which pc you move it to.

---

