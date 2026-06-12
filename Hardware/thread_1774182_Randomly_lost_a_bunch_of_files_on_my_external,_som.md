---
title: "Randomly lost a bunch of files on my external, some help?"
date: 2011-06-03
forum: Hardware
---

### Post by dannelb on 2011-06-03
So, I was setting up Ubuntu on my friend's netbook. The installation went beautifully and was kind of fun actually (haven't done a computer project for a while, so it made me happy). The problem came when I was transferring some of the files on to her netbook (Asus eee).

I was transferring a lot of media files from my WD 320 external hard drive. It was taking a long time and the computer went to sleep in the process. When I turned it back on, things were really messed up. The files were missing from the hard drive. When I look at the hard drive properties, the free space is still the same, so the info from the files must still be there. I guess they somehow got deleted from the filesystem? I'm not entirely sure.

I ran PhotoRec overnight and got some of my files back, though most of them are messed up beyond repair. I've tried it on my own netbook with the same problem. I don't have a way to test it on another kind of computer, as I have only Ubuntu in the house now...I could go bring it somewhere else if anyone thinks this would make a difference.

So, do you have any ideas for other stuff I could do in Ubuntu to get those files back? Is there a special way to mount the hard drive that might cause them to show up?

Any help is greatly appreciated!

---

### Post by dannelb on 2011-06-03
Verifying the partition table with fsck gives this output:

> Command (m for help): v
Partition 1 does not end on cylinder boundary.
Partition 2 does not end on cylinder boundary.
Partition 3 does not end on cylinder boundary.
Warning: partition 1 overlaps partition 3.
Partition 4 does not end on cylinder boundary.
Warning: partition 2 overlaps partition 4.
Warning: partition 3 overlaps partition 4.
Total allocated sectors 2464353615 greater than the maximum 625121217


---

### Post by coffeecat on 2011-06-03
The cylinder boundary messages probably don't matter, but the partition overlaps and the sector figures indicate damage to the partition table. With the drive attached, post the terminal output of:

```
sudo fdisk -lu
```

That will show us what partition table inconsistencies there are. They may be repairable but whether repairing the partition table will enable you to recovery your lost files is another matter. But let's see.

---

### Post by dannelb on 2011-06-03
Here's the output:

> Disk /dev/sdd: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x41ffc810

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63   625121279   312560608+   c  W95 FAT32 (LBA)


I've been trying to use TestDisk. I've gotten a couple files back, but not the ones I really need....

---

### Post by coffeecat on 2011-06-03
The output of fdisk shows just one partition covering the whole disk, so it doesn't confirm the output of fsck. Tbh, I was not aware that you could use fsck to verify a partition table, and there's nothing in man fsck about this - that I could find. How did you get that output from fsck? What exact command did you use?

Also - were you running dosfsck? If this didn't work you might need to think about using a Windows utility. Do you have access to Windows?

---

### Post by dannelb on 2011-06-03
Sorry, I said fsck, but I meant fdisk. So, fdisk is both saying that there is one partition AND that multiple partitions are overlapping? How is that possible?

I didn't try dosfsck...running that now. Don't know how I missed that, let's hope it does something.

---

### Post by coffeecat on 2011-06-03
> **dannelb said:**
> Sorry, I said fsck, but I meant fdisk. So, fdisk is both saying that there is one partition AND that multiple partitions are overlapping? How is that possible?

Did you run testdisk between the two instances of fdisk? Just fyi, testdisk will scan the HD to try to find evidence of partitions. It's not a file recovery app in itself - you have to use photorec for that, which you have done. Testdisk will present you with what partition information it has found and will rewrite the partition table according to what you accept. Sometimes you have to do a deep scan or another scan in testdisk to find all the lost partitions.

But question: before the problem occurred with the laptop, did you have one or four partitions (or some other number) on that drive?

---

### Post by dannelb on 2011-06-03
Yeah, I ran TestDisk between fdisk. I've kind of just been trying to do anything and everything to get these files back...but it's not looking promising.

This drive never had partitions. It's an external that I use only for backup/storage. There was some documents on there, but mostly media files.

---

### Post by coffeecat on 2011-06-03
Well, it probably would have had one partition. You can have a filesystem in a hard drive without partitions, but it's unusual.

My guess from reading that first  fdisk  output, whatever corrupted files inside the filesystem also corrupted the partition table. To have partition 1 allegedly overlapping partition 3, and 2 and 3 overlapping 4 is so extreme it's probably the result of random data being written to the partition table. I thought that was weird when you first posted that output.

OK, assuming that the drive only ever had one partition, I believe that testdisk is not going to achieve any more. It only recovers lost partitions, not lost data. You've already run photorec and you say that some of the files are messed up beyond repair. That may be because they have been partially overwritten, which means they really are beyond repair. Or that may be due to filesystem corruption on a fragmented filesystem and FAT32 filesystems do get fragmented quickly, and photorec is unable to find fragments of the file.

If you don't achieve anything more with dosfsck, it might be worth trying chkdsk from Windows. Or rather, I believe you would use chkdsk. I've never used chkdsk on a FAT32 filesystem so I'm not quite sure whether that's the one to use or whether Windows has another utility for FAT32. Since FAT32 is a Microsoft filesystem, there should be something in Windows for this.

---

### Post by dannelb on 2011-06-03
Yeah, I meant one partition...I think my brain is fried, working on this all day yesterday and today so far...ugh

I'm thinking you're right that I'm not going to get that stuff back. I did try the Undelete thing in TestDisk and was able to get some stuff, but not everything.

It's frustrating, cause I can see the folders. But they are empty. Some of them open and show an empty folder. Others send me back to the main directory of the hard drive. It's very odd.

So, after I toil a little more and decide to give up...how do I get that space back? Will I have to format the hard drive totally? (probably a good idea anyway...)

Thanks!

---

### Post by coffeecat on 2011-06-03
> **dannelb said:**
> It's frustrating, cause I can see the folders. But they are empty. Some of them open and show an empty folder. Others send me back to the main directory of the hard drive. It's very odd.

I'm far from being an expert, but that does sound like filesystem corruption. The allocation table is most likely damaged.

> **dannelb said:**
>  So, after I toil a little more and decide to give up...how do I get that space back? Will I have to format the hard drive totally? (probably a good idea anyway...)

Oh, definitely a re-format after you've rescued what you can. You might want to think about choosing something other than FAT32. It's about the most fragile filesystem still in use. It's only virtue is that everything can read and write to it. Do you have access to Windows? If so, NTFS would be a better choice because it is journalled and more robust. Ubuntu read/write support is reliable for NTFS but you do need Windows (and chkdsk) in case you need to repair it. If you don't have access to Windows, you'd be far better off with a journalled Linux filesystem such as ext3 or ext4. One minor disadvantage of that is that Linux permissions can get in the way and you will need to do some chowning and chmodd-ing on the ext3/4 filesystem. post back if that is what you want to do and you need help with that.

---

### Post by dannelb on 2011-06-03
All my other drives are NTFS. The only reason that this one is vfat is because I use it to connect to the Wii and load videos/games/etc from it. But, I think now the homebrew programs can use NTFS as well, so I might as well switch this one over to that after all is said and done.

I've had a bit of luck with PhotoRec. Got some of my movies back. Didn't get the pictures and TV shows I wanted though...ugh. And of course my connection is limited to 2gb of bandwidth a month...sucks

Anyway, thanks for all your help!

---

### Post by coffeecat on 2011-06-03
> **dannelb said:**
> All my other drives are NTFS. The only reason that this one is vfat is because I use it to connect to the Wii and load videos/games/etc from it.

Yes, of course, I forgot that some devices will only use FAT. I have to use a FAT32 drive to transfer files to/from my Sony PS3.

I'm glad you got some more stuff back. Good luck!

---

### Post by dannelb on 2011-06-08
Phew, finally all over. I got all my pictures back, but lost a lot of my videos and music (makes it so much more frustrating being on a 2gb/month limited connection! Guess I'll just have to wait till my next trip to the States).

I then formatted the drive with ext3 filesystem. I found out that the media player I use on the Wii can read ext3 (not sure if the backup program can yet...). All seems to be working well, let's hope it stays that way.

Thanks for all your help.

---

