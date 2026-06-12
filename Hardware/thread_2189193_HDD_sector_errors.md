---
title: "HDD sector errors"
date: 2013-11-21
forum: Hardware
---

### Post by geohei on 2013-11-21
Hi.

I connected a HDD which holds 2 years old data. This data wasn't read during that time (scrubbing). While trying to copy, I noticed about 10 read errors. I'd like to get these files back.

While using cp, I managed to get 3 of them back after numerous retries. These files were correctly copied since I have md5 checksums from all files. So it seems, that if the HDD first denies access (read error), that doesn't mean that this situation will necessarily persist. Multiple copy attempts could possibly retrieve the complete file eventually.

Here an example of a read error:
```
root@ubuntu:/media/test/# cp -a Flight.txt /media/data/
cp: reading 'Flight.txt': Input/output error
cp: failed to extend '/media/data/Flight.txt': Input/output error
```

I used cp to copy the files. Is there a tool which is more appropriate to copy files with bad sectors?

Thanks,

---

### Post by geohei on 2013-11-22
Hi.

No answers yet ... was the question not clear (shall I rephrase?)?

What about "smartmontools" and/or "badblocks"?
Do these tools include a feature to re-read bad blocks more often than "cp" does?

BTW ... I wonder if the number of read attempts of bad blocks is defined by the tool used (e.g. "cp") or by the firmware of the HDD? Does the OS have an influence upon this behavior?

---

### Post by andyfied on 2013-11-22
Hello

smartmontools will just monitor for errors where as badblocks will attempt to read and possibly fix them. I would NOT recommend using badblocks to repair the files in damaged sectors if you would like to keep the data. If it can't read them, it will cordon that area off then copy the other bits somewhere else permanently corrupting the files. Maybe try copying with dd which does byte level copying and see how it goes. I'm not sure how many times badblocks reads a sector before giving up and moving on.

---

### Post by geohei on 2013-11-23
> **andyfied said:**
> I would NOT recommend using badblocks to repair the files in damaged sectors if you would like to keep the data.
Why? What does badblocks do that would avoid data rescue from bad blocks?

> **andyfied said:**
> If it can't read them, it will cordon that area off then copy the other bits somewhere else permanently corrupting the files. Maybe try copying with dd which does byte level copying and see how it goes. I'm not sure how many times badblocks reads a sector before giving up and moving on.
Ok ... I'll give dd a try.

However it would be important to know if the OS, or the HDD's firmware is defining how many read attempts accur if a bad block is found. If it is the HDD's firmware, dd will end up at the same places than cp.

Can you confirm that the command would be:
```
dd if=/dev/sda1 of=/dev/null bs=512
```

Something about /dev/null above ... As far as I understood, a bad block is remapped to a reserve block if it is read after multiple attempts (threshold). If this theory (!) is correct, /dev/null would be sufficient since the bad block is remapped after successful read. Is this correct?

---

### Post by tgalati4 on 2013-11-23
Your case is a good example of "bit rot", something that happens to magnetic media over time.  The ZFS file system has the ability to "scrub" the files and compare checksums for files that are stored in a few locations on the ZFS disk.  Once your files have suffered from bit rot, it can be nearly impossible to recover them.  You can use special tools to repair music files or photos or videos, but other types of binary files are nearly impossible to repair.  Multiple attempts to read the file can sometimes recover the weak bits, but it doesn't work if the drive has physical defects (from a head crash for example).

Writing to /dev/null just forces the dd command to dump the bits.  This process exercises the read heads and if the drive's firmware detects a bad block, it will presumably move it.  But, this will only work if there is room to store these bad blocks.  When you run out of bad block allocation, then you have real problems.

Running *badblocks* by itself will just put out a list of data blocks that can't be read.  That's helpful for later data recovery.  Using *fsck -cc* will find and mark blocks as bad to the operating system, but this has some issues:  [http://www.linuxquestions.org/questions/linux-general-1/fsck-is-not-removing-bad-blocks-why-not-629467/](http://www.linuxquestions.org/questions/linux-general-1/fsck-is-not-removing-bad-blocks-why-not-629467/)

What is the SMART status of this drive?  Perhaps there are other things failing.

---

### Post by geohei on 2013-11-23
> **tgalati4 said:**
> Your case is a good example of "bit rot", something that happens to magnetic media over time.  The ZFS file system has the ability to "scrub" the files and compare checksums for files that are stored in a few locations on the ZFS disk.  Once your files have suffered from bit rot, it can be nearly impossible to recover them.  You can use special tools to repair music files or photos or videos, but other types of binary files are nearly impossible to repair.  Multiple attempts to read the file can sometimes recover the weak bits, but it doesn't work if the drive has physical defects (from a head crash for example).
I had several huge files which could initially not be read. However after multiple attempts, they were read and correctly restored (md5 checksum previously done matched). However this didn't apply to all files - only about half of them.

> **tgalati4 said:**
> Writing to /dev/null just forces the dd command to dump the bits. This process exercises the read heads and if the drive's firmware detects a bad block, it will presumably move it. But, this will only work if there is room to store these bad blocks. When you run out of bad block allocation, then you have real problems.
Yes, it was my intention to exercise the read heads since I managed to previously retrieve bad blocks like this.
These bad blocks are only moved if retrieved successfully, right?
Or are bad blocks reallocated to some spare position on HDD without moving its data?

AFAIK, bad blocks are only discovered if data is read. That's the reason why scrubbing exists. However I never really got when bad blocks are in fact reallocated. Is it when bad blocks are read after x attempts (in this case, data would be copied) or is it if bad blocks aren't read after x attempts (in this case, the file would be corrupt) ... ?!

How do I know that I still have room for bad blocks? SMART?

> **tgalati4 said:**
> Running *badblocks* by itself will just put out a list of data blocks that can't be read. That's helpful for later data recovery. Using *fsck -cc* will find and mark blocks as bad to the operating system, but this has some issues:  [http://www.linuxquestions.org/questions/linux-general-1/fsck-is-not-removing-bad-blocks-why-not-629467/](http://www.linuxquestions.org/questions/linux-general-1/fsck-is-not-removing-bad-blocks-why-not-629467/)

What is the SMART status of this drive? Perhaps there are other things failing.
I can't access SMART since the HDD is presently connected to the system via a RAID controller, which doesn't allow SMART data requests to connected HDDs. The RAID controller is an (old) ICP PCI bus card.
```
root@ubuntu:~# smartctl -x /dev/sda
smartctl 5.41 2011-06-09 r3365 [i686-linux-3.2.0-23-generic-pae] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

Vendor:               ICP
Product:              Host Drive  #00
Revision:
User Capacity:        2,000,355,194,880 bytes [2.00 TB]
Logical block size:   512 bytes
scsiModePageOffset: response length too short, resp_len=13 offset=12 bd_len=8
>> Terminate command early due to bad response to IEC mode page
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.
```

---

### Post by andyfied on 2013-11-26
> Why? What does badblocks do that would avoid data rescue from bad blocks?

Badblocks, like CHKDSK will find a bad sector (one it can't read) then it will flag that sector as bad and won't allow anything to read it again. It might move the rest of the readable but failing sectors to good sectors then you will have an unpleasant jigsaw puzzle!

> However it would be important to know if the OS, or the HDD's firmware is defining how many read attempts accur if a bad block is found. If it is the HDD's firmware, dd will end up at the same places than cp.

True. I am unsure, but it is worth a try since it is non-destructive.

> Can you confirm that the command would be:
```
dd if=/dev/sda1 of=/dev/null bs=512
```

Something about /dev/null above ... As far as I understood, a bad block is remapped to a reserve block if it is read after multiple attempts (threshold). If this theory (!) is correct, /dev/null would be sufficient since the bad block is remapped after successful read. Is this correct?

Bit unsure about that one, I'll see if I can find out and get back to you. My recommendation is to do your best to get a good copy and don't move anything on a drive with many bad sectors.

---

### Post by geohei on 2013-11-26
> **andyfied said:**
> Badblocks, like CHKDSK will find a bad sector (one it can't read) then it will flag that sector as bad and won't allow anything to read it again. It might move the rest of the readable but failing sectors to good sectors then you will have an unpleasant jigsaw puzzle!
Well ... in this case, badblocks would be a bad idea for me, since I managed with cp to copy some important files. As far as I understand, badblocks (which I didn't use) would have flagged these sectors as bad, hence not allowing cp to access them anymore.

To make it short, the drive we are talking about died completely after a nightly powerdown! I had this some months before already. If a drive is marginal, I believe it is wise to keep it powered all the time while trying to get data back. This might just be a wild stupid guess, but I noticed this already several times in the past.

> **andyfied said:**
> Bit unsure about that one, I'll see if I can find out and get back to you. My recommendation is to do your best to get a good copy and don't move anything on a drive with many bad sectors.
Yes, I get 99% of the data back! Hence, my tests on the remaining 1% were more for educational purpose rather than desperate attempts. However it would be good to know how long the drive (with and without TLER) tries to get access to the data on the bad block.

---

### Post by andyfied on 2013-11-28
> **geohei said:**
> Welll ... in this case, badblocks would be a bad idea for me, since I managed with cp to copy some important files. As far as I understand, badblocks (which I didn't use) would have flagged these sectors as bad, hence not allowing cp to access them anymore.

Yeah, that's it.

> **geohei said:**
> 
To make it short, the drive we are talking about died completely after a nightly powerdown! I had this some months before already. If a drive is marginal, I believe it is wise to keep it powered all the time while trying to get data back. This might just be a wild stupid guess, but I noticed this already several times in the past.

 This is often the case for very sick drives.

> **geohei said:**
> 
Yes, I get 99% of the data back! Hence, my tests on the remaining 1% were more for educational purpose rather than desperate attempts. However it would be good to know how long the drive (with and without TLER) tries to get access to the data on the bad block.

Reading the same sector over and over is much more likely to cause a head crash than random reads over the whole drive (which is why I was unsure about running dd over the same area). The head just flicks back and forth getting hotter and more fatigued until *scraaaaaape*. I'm a junior tech in a data recovery company (yes, a genuine one; no, I'm not going to be advertising here) and I know our equipment moves the heads in such a way to allow them to cool off and not put too much stress on them. We normally try to read the bad blocks twice before stopping and making a decision as to what to do next, but that's all custom software and hardware, plus decades of experience from each of the senior technicians and their knowledge of each model of drive.

I'm glad you got back what you needed!

---

### Post by efflandt on 2013-11-28
Normally a drive has reserved sectors that it remaps in place of bad sectors automatically and transparently and will attempt to copy the data from the bad sectors to the remapped sectors. When you actually start seeing bad sectors it typically means that all the error sites are used up, and the drive will only get worse. That is time to get what you can from the drive if you have not already backed up the data, before you can no longer read it.

You never know when that is going to happen. I have (rarely) had drives fail under warranty and the warranty replacement last indefinitely. One is in a headless Celeron 300 that has been running SuSE 8.2 for 10 years (2003-05-17), including 5 years 24/7 without rebooting from July 2006 until I shut it down for what ended up being a 14 hr power failure July 2011. I recently had the far end of 3 year old desktop drive begin to fail (Linux partition), it kept going into readonly mode. e2fsk -cc took a long time, but kept it working for a while. But eventually more sectors started going bad and the drive had to be replaced.

---

### Post by geohei on 2013-11-29
> **andyfied said:**
> Reading the same sector over and over is much more likely to cause a head crash than random reads over the whole drive (which is why I was unsure about running dd over the same area). The head just flicks back and forth getting hotter and more fatigued until *scraaaaaape*. I'm a junior tech in a data recovery company (yes, a genuine one; no, I'm not going to be advertising here) and I know our equipment moves the heads in such a way to allow them to cool off and not put too much stress on them. We normally try to read the bad blocks twice before stopping and making a decision as to what to do next, but that's all custom software and hardware, plus decades of experience from each of the senior technicians and their knowledge of each model of drive.
The temperature story is pretty known. Some even say to put the drive into the fridge for 30 minutes. I tried to simulate the same in letting the drive cool down to temperatures #5 degrees (window open :) ). No bad blocks were readable, not even the one which could be read previously after #5 seconds! After it came back to normal temperatures, it worked much better than for the cold ones. After it really heated up, it even went much better. Under these temperatures, I virtually got back the 99%. So ... the heads were stressed maximum when success was maximum. Might be an exceptional situation but that's the way it was!

---

