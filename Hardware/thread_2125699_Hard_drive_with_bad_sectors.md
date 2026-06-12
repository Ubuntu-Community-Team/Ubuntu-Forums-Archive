---
title: "Hard drive with bad sectors"
date: 2013-03-14
forum: Hardware
---

### Post by partloer on 2013-03-14
I have a hard drive with bad sectors I will replace this then install the OS.  I am wondering can the hard drive with bad sectors be used again but not use the bad sectors?

---

### Post by slickymaster on 2013-03-14
Typically, when a HD starts developing bad sectors, it means that it'll die soon and you should toss it. It's possible to low-level scan it with the manufacturer's software and mark the bad sectors so you can continue using it for a while, but eventually more bad sectors will develop and you'll be in the same situation again.

A possible workaround, instead of marking the bad sectors, would be to only partition known-good space, leaving a large buffer of unused disk space around the defects. Imagine that when scanning your hard drive you run into badblocks at 20% of the scan. Then you would partition the disk from 0% to 15%, then from 25% to the end. Run into badblocks again on the second partition at 60% of the scan. You delete the second partition, and remake it from 25% to 55%. Repartition the rest. You keep doing this until there's no more space on the disk.

In result you would have much less available space than a simple bad sector scan-and-mark, and several small partitions which may or may not be a pain to manage, but it absolutely ensures that the heads won't stay for long in spaces where magnetic damage has occurred (they obviously can't be prevented from flying over them while looking for other data).

---

### Post by ahallubuntu on 2013-03-14
~

---

### Post by partloer on 2013-03-14
Thanks both of you for your help.  

I did a SMART report which is how I confirmed that it was a bad hard drive.  I will see if I can export it and post it.  I like the idea of marking the bad sectors and creating partitions.  I know that I cannot rely on the drive so I am getting a new hard drive but was wonder if I could still use it for backup or do something like a RAID 1 to add a level of redundancy.  I already have this computer backup to another to be sure my data (digital photos) is protected.  

Also is it likely that this could have been caused by power failures?  My house has been having several power outages recently (I will buy a backup battery to prevent this in the future) and the hard drive is only three years old.  

Finally, any recommendations what type of hard drive to use?  The computer is mostly used for surfing the web and other basic programs like photo editing, basic word processing, and streaming video shows.  Most space is taken up by a lot of photos.  Possible options are:
 just get another standard hard drive
get a SSD in addition to a standard hard drive
or I heard about the hybrid SSD + HDD

Thoughts?

---

### Post by deadflowr on 2013-03-14
> **partloer said:**
> I have a hard drive with bad sectors I will replace this then install the OS.  I am wondering can the hard drive with bad sectors be used again but not use the bad sectors?

Depends on how many bad sectors.

If it has something like 5, or 10, or 20 bad sectors, and the bad sector count isn't growing, then I'd say you could still use that disk.

Unless it's something that can be fixed with a reformat, those bad sectors are gone anyway, so don't worry about using them again.

---

### Post by ahallubuntu on 2013-03-14
~

---

### Post by slickymaster on 2013-03-15
> **ahallubuntu said:**
> What's your backup/archive system?  If this computer will be both a desktop computer and your "archive" computer (the main place you save all your data), I'd probably get one small drive for the OS - maybe an SSD - and two larger drives for data - with one backing up the other one.  (You could do it as a RAID mirror, but that protects you only against drive failure, not filesystem corruption or accidental erasure.)  Backup the OS drive to your data drives.

If you have your data stored elsewhere and this is just a "client" computer, then I'd get the fastest drive you can afford - a hybrid drive might work well, if you really need that much space.

FYI, as I was trying to explain above: your hard drive itself already has the technology built in to "mark the bad sectors" so you don't have to.  That's what those reallocated sectors are, if you have any.

+1
That would certainly be my approach.

---

