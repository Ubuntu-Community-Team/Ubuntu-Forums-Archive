---
title: "Filesystem for 1TB external HDD"
date: 2013-03-25
forum: Hardware
---

### Post by Ubunterrific on 2013-03-25
I know there are loads of posts all over the internet about what filesystem people would recommend for their external harddrives, but since we're now a fair bit into 2013, i was wondering what the consensus is.

Ok, so i have my WD 1TB 'passport' and use it to back up everything. 

It came as NTFS, but i never come into contact with windows pcs and don't much care for having to justify putting support for it into my custom kernels when there are likely better alternatives. I'd like to avoid it like the plague.
I've had it as FAT32 for a while (thanks to gparted), but i've seen some odd behaviour with the files on it probably fragmenting a bit (i do a lot of transfers now and then).
Tried ext2 briefly but had some problems getting access to it and it sectioned off ~16GB for itself (i do remember reading something about ext formats saving a small percentage of the disk for something, so FAT32 was certainly better in that respect in terms of maximising the disk capacity for my files.)

So the flash-friendly filesystem (F2FS) is now part of the stable kernels and i've used f2fs-tools to (scarily rapidly) format the drive to f2fs; included support for it in the kernel and made a slight tweak to /etc/fstab to mount it on /mnt/f2fs with a command, and i can access it and store things on it in spite of the obvious fact that it's a new filesystem so doesn't get the immediate recognition the average user is used to when using a usb device.

The key thought i have is: F2FS has some pretty impressive benchmarks and even gives ext4 a run for its money, but how stable is it really? I'd hate to lose what i'm about to put on my newly formatted drive?
Ext2 is good in that it doesn't journal, and i know you can get ext3/4 to not journal but is it ideal?

There are a multitude of formats of course, but it's 2013 now and so what i suppose i'm really asking is....What are you guys using? :P

---

### Post by dabl on 2013-03-25
If you don't need to interface with Windows computers, then I see no reason to NOT use ext4.  I have three external drives for backup purposes, and all are ext4 filesystems.

---

### Post by Cheesemill on 2013-03-25
+1 for ext4.

If you're just using it as a data drive you can change the amount of reserved space from 5% to 0% with the following command (when the drive isn't mounted)...
```
sudo tune2fs -m 0 /dev/sdXX
```
This will reclaim the 50GB of space that would have otherwise been reserved.

---

### Post by oldfred on 2013-03-25
Why would you even think about a large file system without a journal. File system repairs after powerfailure or accidents become very difficult or impossible without a journal. Of course you do not need it until you really do need it. 
And yes the journal uses space also. Linux' ext4 reserves space for the journal up front.

Only if you have Windows so you can regularly run chkdsk and if you need compatibility with Windows should then you consider NTFS, but not FAT32. Non-journal system is ok for small drives like most flash drives or camera cards, but even new large flash drives should not be FAT32.

---

### Post by Ubunterrific on 2013-03-26
Thanks, guys. :) Ext4 it is then. Ahhh that's the command to reduce the 5% to 0%.

Well IIRC and you'll have to excuse me for not citing a source for this info, but avoiding journalling reduces the number of writes and so prolongs the drive's lifespan a little bit <- sounded favourable. 

On a side note, f2fs seems to be a bit faffy for endusers at the moment, but ultimately i didn't find any problems in the time i've been playing with it. I think it's got potential. :)

---

### Post by dabl on 2013-03-26
> **Ubunterrific said:**
>  avoiding journalling reduces the number of writes and so prolongs the drive's lifespan a little bit <- sounded favourable. 


I have a Quantam Fireball EL 5.1GB hdd that says journalling is not a problem on hard drives.  ;-)

---

