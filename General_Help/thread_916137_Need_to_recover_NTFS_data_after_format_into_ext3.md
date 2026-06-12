---
title: "Need to recover NTFS data after format into ext3"
date: 2008-09-10
forum: General Help
---

### Post by gerardlouw on 2008-09-10
Hi guys,

My friend recently asked about Linux and I guess I threw him in at the deep end a bit too soon. He managed to unintentionally format his entire hard drive, which was at the time a single NTFS partition. He formatted it into ext3 using the Ubuntu installer. All he has done since the format is install Ubuntu. He had some important data (which wasn't backed up, of course) on the Windows partition and asked me if I could get it back for him. I've experimented with data recovery in the past, but I've never heard of recovering data after formatting into a different filesystem. Is this possible? If so, how?

Thanks a lot for any help
G

---

### Post by -Zeus- on 2008-09-10
My vote is for not possible;  I think the format would blow away anything you could hope to salvage.

---

### Post by NullHead on 2008-09-10
It looks rather grim ... there are a few companies around that do professional data recovery. You might look into [http://www.datarecoverylabs.com](http://www.datarecoverylabs.com/index.aspx?agent=google).

I have no experience with data recovery, but my opinion on the matter is that the data is lost.

EDIT: Just read through that link a bit more ... I think it might be a bit of overkill for a a regular person with a regular computer.

---

### Post by mb_webguy on 2008-09-10
Well, technically the data's still there, even if only as a magnetic afterimage.  But reformatting the drive and overwriting new data means that it's unlikely you're going to be able to get anything useful off of it unless your initials are NSA.

You can give TestDisk a try, but good luck on it finding anything....

---

### Post by cariboo on 2008-09-10
You might want to give testdisk a try, it is available here:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Jim

---

### Post by gerardlouw on 2008-09-10
Thanks guys. I'll definitely have a look at TestDisk. I'd just like to stress the fact that he hasn't actually done anything other than install Ubuntu. Theoretically most of his data should still be there and recoverable. My biggest uncertainty is about doing a cross-filesystem recovery.

G

---

### Post by gerardlouw on 2008-09-11
Bump for any other suggestions?

---

### Post by candyman9999 on 2008-10-03
Dear friends,

Even I have made the same mistake. I am being told that the following can also help; however, I am yet to try it.

(a) Hiten boot disk 9.6
(b) All_Nucleus_Kernel_Recovery_Software.rar

Both seem to be on rapidshare.

Please let me know if some good solution emerges.

---

### Post by Sef on 2008-10-03
> Thanks guys. I'll definitely have a look at TestDisk. I'd just like to stress the fact that he hasn't actually done anything other than install Ubuntu. Theoretically most of his data should still be there and recoverable. My biggest uncertainty is about doing a cross-filesystem recovery.


As long as your friend does not use the hard drive, all or most of the data should be recovered.

---

### Post by hyper_ch on 2008-10-03
Photorec has also a few time been recommended... but the best way is to use your backups to get your files back - I hope you do make regurarly backups.

---

### Post by vikrant82 on 2008-10-03
Why don't you reformat the partition with NTFS and run a regular recovery tool like GetDataBack for NTFS or R-Studio etc.

---

### Post by matey3 on 2008-10-06
It is my experience that when we format a disk the OS only changes the FAT or file allocation table. If we do a long format(low level format)or format via CMOS or as case of scsi/ the scsi cards format (which is similar to the low-level format) then it over-writes every sector with a 0 and that is why it takes so long...and that will make it very hard or near impossible to recover data. and in most cases in the old day if you formatted a disk via cmos(bios) then it also would write over the manufacturer's data which bios use to read to know the number of heads/sectors etc.. and that would leave the disk unusable for good!(In SCSI disk case it was different. it left the disk usable)

so I think the same as others who believe the data is still there now how we gonna get it is another question. I think the software they recommended is a good start. I used to use the norton until way back but have not done any thing like this for a while?
I also used the Partition Magic program a few times before and were able to recover old partitions? (if all else failed I guess u can try PM)?
 
Good luck and thanks to all for sharing the info!

---

### Post by jerome1232 on 2008-10-06
Testdisk can recover partition tables but since you've written to the disk I don't think that'll work, you'll need to do some file carving. I've heard foremost and photorec are good programs for this. If you check out [this]("https://help.ubuntu.com/community/DataRecovery") page it'll give some more options and give some examples of how to search through and rename what the program you choose to use finds. (they won't have their original file names intact)

---

### Post by fusebox on 2009-02-15
Hello ppl

Has anyone found a solution to this?

I just found myself in the similar problem. In this case, the hard disk has 2 partitions - 1 - Vista and 2 - Hp Recovery.

firts partition was NTFS then accidentaly quick formated to ext3 (the partitioner crashed during the process)

The machine couldnt boot afterwards, then i polayed around with cfdisk, ptdd and lost the HP recovery partition (reads as free space)

Now theres no f11 recovery functionality

Could anyone help please?

---

### Post by joshxdr on 2009-04-23
I had the exact same problem as the original poster, luckily I ignored most of the posters on this board and I RECOVERED MOST OF MY DATA.  I completely wiped out a whole disk that had NTFS file system and installed Ubuntu linux with ext3 and installed about 1G worth of software under ext3.  I had about 60G of data on the original disk, so only a very small fraction of the actual sectors had been overwritten.  A recovery service will charge you minimum $500, but if you have time you can do it yourself.  You need to buy software that can recover NTFS partitions.  Don't waste your time with "data recovery" software since this is for recovering deleted files, not partitions.  The software I used is crap called "Data Doctor Recovery NTFS".  Do not buy this software, I learned late in the game there are better competitors.  You will lose a lot of the original directory structure, but some of the folders and most of your files will still be there.  Obviously, once a sector is overwritten the data is lost forever.  I was lucky that I had only written a small amount of data under ext3, so most of the original NTFS files were still intact.

It is interesting that so many of the previous posters on this thread stated that this was not possible.  My future advice to these ... hrmmm ... "gentlemen" is that is that if you don't really know, please don't post hearsay or guesses, it is not helpful.

---

### Post by ubu-for on 2009-04-23
Fine, but which program would you finally recommend?

I like Testdisk including Photorec.

[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

### Post by BlasterXL on 2009-04-23
Thank you all for these posts! It helped me allot to recover my files. The problem is I'm pretty new to Ubuntu, but this worked for me.

For **noobs** like me, I tell you how I recovered NTFS Data with TestDisk step by step in Ubuntu 9.04:

**Step 1: Installing TestDisk**
- Start the console somewhere in applications. (Or press Alt+F2).
- Type this: *sudo apt-get install testdisk* (insert your password).
- Ok Done.

**Step 2: Starting / Recovering with TestDisk:**
- From the console type: sudo testdisk (insert your password).
- Maximize the window.
- Select: [Create] 
- Select: (in my case): [Disk /dev/sda - 1000 GB / 931 GiB] ...
- Select: [Intel  ]  Intel/PC partition
- Select: [ Advanced ]  Filesystem Utils
- Select: [Boot]
- Select: [Rebuild BS] (Rebuild boot sector)
- Select: [List]
- Finally, I see my files and directories, now you can copy them easy by pressing the C button. The files will be located in your home directory, after that you can copy them with ease to an another drive.

I hope it helped someone!
Greets, from Holland, and sorry for my bad English!

---

### Post by joshxdr on 2009-05-02
I reformatted an NTFS partition with ext3 on a pc with two HDDs.  I recovered NTFS data from the disc reformatted with ext3.  Since I still had windows bootable from one of the two disks, I chose to recover using windows sw rather than Linux sw.  The sw I used was Data Doctor Recovery NTFS, but after reading the reviews in CNET it looks like R-Studio and others have better tools and are less buggy.  It is important to remember that file systems are record-keeping systems that track what files are where.  File data is recorded to sectors on the disk.  As long as all the sectors for a file are not overwritten, the file should be recoverable.

---

