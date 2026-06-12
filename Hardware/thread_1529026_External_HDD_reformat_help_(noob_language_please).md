---
title: "External HDD reformat help (noob language please)"
date: 2010-07-11
forum: Hardware
---

### Post by captainron042 on 2010-07-11
I've seen that this question has been asked, but I can't seem to find any info that's newer than a year old.

I have an External HDD that is 2TB. It is currently just over 1TB filled already, and it has come to my attention that the headache of a 4GB max filesize has a solution: reformat to another filesystem. (I have a lot of movies)

I also have learned that it is possible to reformat the HDD without loosing any of the files still on there, which is good, because I don't have any more 2TB HDDs laying around not being used!

I use it 99% of the time with my Ubuntu machine, but I don't want to look like an idiot if I ever tell a friend to hook his Windows machine to my HDD and it doesn't work. However, if a certain filesystem is much, much better to use strictly with Ubuntu, I don't suppose I would mind transferring them to a thumbdrive and handing it to him several times, letting my computer be the middle man.

That being said, what would be the best filesystem type? From the old info I did find, it seemed that NTFS is buggy. Is it still? I also heard that EXT3 does not have an undelete capability, and that files get corrupted.

Next, what is the best way/program to use to reformat the HDD, being sure that I don't loose any files?

Much Thanks!

---

### Post by AltomineUK on 2010-07-11
What's the current type of Filesystem used on your External?

---

### Post by captainron042 on 2010-07-11
W95 FAT32 (0x0b), according to the Disk Utility

BTW, My pc has 5 partitions, 
     DellUtility 58MB (FAT32), 
     OS 5.4GB (FAT), 
     238GB ext3 (Linux 0x83), 
     Extended 6.2GB (Extended (0x05)),
     6.2GB Swap (Linux swap (0x82))

My Dell Laptop has a similar configuration. Does anyone know what those last two partitions are for? Are they wasted memory that I can delete?

---

### Post by JustinR on 2010-07-11
Hi captainron042!

I've never had issues with NTFS before but if you're having issues with it and FAT32 (the filesystem currently on your external HDD) is a headache I would go with EXT4. Its the newest EXT filesystem type and has been very reliable for me. It's a Linux only filesystem, so it won't work with Windows but I've never had corruption issues with it or anything like that - and there isn't 4GB file limits like FAT32.

---

### Post by chessnerd on 2010-07-11
I am pretty noobish about reformatting myself, but an idea has occurred to me that might work: repartition in segments:

First, repartition just 500 GB of it to NTFS or ext4 (NTFS if you want to use it with Windows, ext4 if you only want to use it with Ubuntu) by shrinking the FAT32 partition to 1.5 TB and reformatting the newly unallocated space to the filesystem you want. Then, move 500 GB worth of files over to the new partition.
Then, expand the size of that partition to 1 TB the same way and move 500 GB more. Expand it again to 1.5 TB and move the rest of the files. Then, expand it to the full 2 TB.

I have never had any issues with resizing filesystems, and I've done it on several computers several times and have never lost data. However, I have heard others say that a resize made them lose data. 

If no one else suggests anything else though, this just might work.

Note: It would be a good idea, if you do do this, to defrag the drive a couple of times first. It should help in not losing data.

EDIT: Also, if you go with this plan, deallocate space starting at the END of the drive, not at the beginning.

---

### Post by captainron042 on 2010-07-11
Thanks, Justin, I've never had issues with NTFS, but a few old (2006) threads say they did, like it was buggy with Linux. I dunno if this has been fixed. :/ 

And that's kinda what I was imagining I'd have to do, Chessnerd. Although the threads I saw made it sound like reformatting using a simple command would do this automatically. How do you defrag with Ubuntu? I have never defragged Ubuntu, and I was under the impression that you didn't have to because of the way it saved files.

---

### Post by chessnerd on 2010-07-11
> **captainron042 said:**
> And that's kinda what I was imagining I'd have to do, Chessnerd. Although the threads I saw made it sound like reformatting using a simple command would do this automatically. How do you defrag with Ubuntu? I have never defragged Ubuntu, and I was under the impression that you didn't have to because of the way it saved files.

I've never heard of a command that would do anything like that. What I was suggesting was getting a [GParted LiveCD]("http://sourceforge.net/projects/gparted/files/gparted-live-stable/") or installing GParted in Ubuntu and doing this manually. Then, you load that up, hook up the drive and begin partitioning it. (Note: you need to unmount the drive before it can be partitioned)

As for defragging in Ubuntu, you are correct in that you don't need to defrag Linux filesystems, however, this drive was formatted as FAT32, which is even more prone to fragmentation than NTFS (the current Windows filesystem). To defrag it, your best bet is to boot into a Windows install and do it there. As far as I know, there are no defrag programs for Linux.

If you haven't been doing a lot of writing to the drive then this won't matter as much because it likely won't be too fragmented, however, if you regularly were deleting and adding files then it it likely quite fragmented. If you can't get access to Windows, I wouldn't worry about it too much. I only suggest it because that is what I always did before I reformatted my drives.

Also, I've just remembered something - If you have access to a Windows XP machine, then you could actually use it to convert your entire drive to NTFS without losing any data, as explained here: [http://support.microsoft.com/kb/307881](http://support.microsoft.com/kb/307881)

I've found writing to NTFS to be fine in Linux, and have never personally experienced any errors, however, again, this is just the experience of one user. I do know that NTFS writing has improved a lot in recent years.

If you have any other questions, let me know.

---

### Post by AltomineUK on 2010-07-12
On a final note, the ext3 has some 64-bit memory limitations. Ext4 can support upto something like 1 exabyte, which is "quite" big and is backwards compatible with previous types of filesystems.

---

### Post by captainron042 on 2010-07-12
Good! I was planning on joining all of my movies into 1 gigantic file, so that would work!

(j/k)

Any big benefits between NTFS and EXT4? Other than EXT4 does not work with Windows? Is one more efficient?

---

### Post by AltomineUK on 2010-07-12
> **captainron042 said:**
> Good! I was planning on joining all of my movies into 1 gigantic file, so that would work!

(j/k)

Any big benefits between NTFS and EXT4? Other than EXT4 does not work with Windows? Is one more efficient?

Apart from the fact that Windows might complain about Ext4 being "different and weird" and refusing to read from it (or recognise it for that matter), Ext4 on Linux does not require defragmentation (because Linux automatically defragments upon detection), unlike NTFS. That said NTFS has come a long way so even though it requires defragmenting..... you do not need to perform it as frequently compared to earlier versions and it's less buggy with Linux. My external's NTFS and NTFS bugs are unheard of on my Linux system.

Ext4 supports huge amounts of memory space. Now you might think that it will take loads of time to run a filesystem check, but it doesn't. It takes a lot less time than it would because it runs fsck that skips any unallocated memory blocks. If you want HIGH PERFORMANCE you can consider another Linux filesystem called XFS (supports 8 exabytes.)

If you are looking to use your external for simply trading files between different OSs, go for NTFS as it can operate between all the major OS's (Mac, Windows, Linux....) quite easily, but please note that NTFS has limitations on File Size and Volume Size amongst other small things.

Of course there are many many other points to consider if you want to pick THE BEST, but I think this will do for now.

---

### Post by captainron042 on 2010-07-12
Awesome info! I believe I'll be using EXT4, then. I am curious about the High performance, though, but I haven't heard anything about it until now, which makes me wary of any potential problems.

Thanks to all of you for the help. I just finished downloading Gparted, so I will try this out promptly.

---

### Post by captainron042 on 2010-07-12
While I am using my wife's Acer AspireOne to defrag my external HDD, does anyone have any answers for my other curiosity?

> My pc has 5 partitions, 
DellUtility 58MB (FAT32), 
OS 5.4GB (FAT), 
238GB ext3 (Linux 0x83), 
Extended 6.2GB (Extended (0x05)),
6.2GB Swap (Linux swap (0x82))

My Dell Laptop has a similar configuration. Does anyone know what those last two partitions are for? Are they wasted memory that I can delete?

---

### Post by dino99 on 2010-07-12
here is info about ntfsprogs (into synaptic)

The Linux-NTFS project ([http://www.linux-ntfs.org/](http://www.linux-ntfs.org/)) aims to bring full
support for the NTFS filesystem to the Linux operating system.

This is a set of tools targeted for people interested in working
with the NTFS support in the Linux kernel and using it.  The
following utilities are included:

ntfsfix - Fix common filesystem errors and force Windows to check NTFS.

mkntfs - Format a partition with an NTFS filesystem, optionally bootable.

ntfsinfo - Show some information about an NTFS partition or one of the
files or directories within it.

ntfslabel - Show, or set, an NTFS partition's volume label.

ntfsresize - Resize an NTFS partition without losing data.

ntfsundelete - Recover deleted files from an NTFS partition.

ntfscluster - Locate the owner of any given sector or cluster on an NTFS

of course, there is no problem working with ext* filesystem and ntfs (both ways using fs-drivers)

---

### Post by AltomineUK on 2010-07-12
The 6.2 GB is the SWAP partition. If you have a keen eye, you will notice that the swap will not appear amongst your other filesystems when you double-click the "Computer" icon.

The SWAP is used by your computer to prevent one of the most scariest situations that can happen on your system (it's also used for other things but we'll stick to basics)....running out of RAM memory, which happens when you run too many programs (well I find it scary anyway). Using the SWAP, if you ever run out of memory from your main RAM, the computer will automatically switch to the SWAP to keep on running and keep its users comfortable. I would recommend you don't even attempt to change that unless you know what you are doing. 

The computer chooses the size SWAP file automatically upon installation based to your main RAM's capacity. It might have chosen 6GB because you might be having a low capacity RAM. For all these reasons please don't delete your SWAP.

---

### Post by captainron042 on 2010-07-12
good reason!

So, I partitioned my HDD to EXT4 and there are now two parts of the drive. The computer "sees" two seperate drives, but when I open the new one, I have no permissions to write to the drive. There is also a folder called lost+found that is unreadable, even by right-clicking.

---

### Post by captainron042 on 2010-07-13
any help with this little issue? Is this normal?


thanks

---

### Post by AltomineUK on 2010-07-13
lost+found directory is where your Linux system saves files during a failure....again one of those things best left untouched.....the reason why it won't let you read it is because it's contains critical data and is a safety feature (a bit like the SWAP), although you can access it as the root.... as for the two drives, can you state their names please?

---

### Post by captainron042 on 2010-07-13
That makes sense. I knew I could probably get access to it using sudo, but I shouldn't have to in order to operate the entire partition outside of the Lost+Found folder, lol.

The original drive is called FANTOM (FAT32, and the new partition is Fantom1(EXT4).
 Thanks for your help

---

### Post by captainron042 on 2010-07-14
You know, I just opened the Disk Utility, and used the format function on that partition, and it works now.

---

### Post by AltomineUK on 2010-07-14
Yea that helps too..... Cool!!

---

### Post by captainron042 on 2010-07-16
Guys, I have a big problem now. I got the EXT4(Fantom1) partition working, and moved the files over from the fat32(FANTOM) partition in three increments. After all of the files were in the new partition, I opened Gparted again and told it to delete fat32 partition and extend EXT4 to take up the rest of the space. 

Now, after rebooting my computer, only one partition loads; FANTOM, which should have been deleted! The file browser shows no files or folders, and says free space 230.5 GB (on a 2TB drive).

Gparted shows two sections, 
Partition - /dev/sdb2   File system - fat32   Mount Point - /media/FANTOM_   Label - FANTOM   Size - 1.59 TiB   Used - 1.37 TiB   Unused - 230.5 GiB
Partition - unallocated   File system - unallocated   Mount Point - blank   Label - blank   Size - 230.53 GiB   Used - ---   Unused - ---


Can someone help me save my files?!!   The Ext4 partition was the majority of the drive before my last Gparted session, why is it now listed as fat32? It says there is used space, why can't I see my files? I also plugged it into a windows computer, but windows didn't show any sign of recognition, although the drive made a sputter noise and the light blinked (signaling that it knows there should be a connection?)

---

### Post by captainron042 on 2010-07-16
I ran the long version of "Check Filesystem" in the Disk Utility, it says Completed OK.

I right clicked the partition in Gparted, and was able to move/resize. I told it to make the partition with the files on it take up the entire drive. It worked for a second, then said that there is an error because the drive is locked. When I said OK, and the script window went away and back to the Gparted screen, the partition stretches across the whole drive. But I still cannot open it.

---

### Post by captainron042 on 2010-07-16
One more reboot, and I find that it's gone. All gone. 

Guess I should have followed the advice that the prompts gave me: back up all data before proceeding. What I should have done, while probably unethical, is buy a 2TB harddrive from Best Buy, back everything up and reformat the old drive, transfer everything back and take the Best Buy hard drive back.

You live, you learn.

---

### Post by SebX86 on 2010-07-17
Pay attention that you will never get high write speeds on NTFS filesystems (due to the ntfs-3g module).

If you work with Linux only, copy all your files elsewhere. Format your hard drive and put all your data back on your external hard drive.

---

