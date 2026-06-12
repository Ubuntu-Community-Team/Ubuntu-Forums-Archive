---
title: "Repurposing an old fat 32 external Hard Drive."
date: 2021-06-11
forum: Hardware
---

### Post by rsteinmetz70112 on 2021-06-11
I have an old external backup drive that I'm attempting to repurpose. It is a 2TB USB3 Desktop drive with external power supply.

I've tried to run chkdsk on it on a Windows machine and Windows 10 doesn't seem recognize the partitional table. (dosfsck identifies as gpt)

Running ls simply bombs out after a string of I/O errors.

smartmon gives output and reports the disk is good.

dosfsck and fsck.vfat seem to recognize the partition and provide some data but don't appear to complete according to the sample output I see online. A number of directories seem to be corrupt and a generate a disk Input/output error (5). 

rsync appears to be able to copy most of the files but also gets the disk I/O error on some directories.  rsync copies the corrupt directories but not their contents.

It occurs to me the FAT is corrupt.

Any ideas?

---

### Post by Autodave on 2021-06-11
If there is nothing on there that you need, why not just reformat it to NTFS if being share with Win machines?  Then check it for errors.  If none found, use as a secondary backup.

---

### Post by TheFu on 2021-06-11
I'd use **gparted** to lay down a fresh GPT, then create an EXT4 partition.  With a native Linux file system, all sorts of backup options become possible.  Good thing is was just a backup partition.  Nothing important on it as primary.

---

### Post by scorp123 on 2021-06-11
> **rsteinmetz70112 said:**
> It occurs to me the FAT is corrupt.
Not really surprising, is it? In my experience FAT filesystems get corrupted rather easy.

> **rsteinmetz70112 said:**
> Any ideas?

If nothing important is on that disk: Nuke that FAT filesystem and replace it with something more reasonable. NTFS if you intend to share it Windows machines, or Ext4 if you only intend to use it with Linux.

---

### Post by rsteinmetz70112 on 2021-06-12
Thanks. 

I don't really know what is on it and I can't tell too much because the filesystem is so screwed up. 
I also did try to convert it to NTFS and that failed as well. I got an error about not enough memory, not sure how that works since the computer had 8GB of RAM and plenty of disk space. Possibly because it's a 2TB dirve?
My plan was to evaluate the stuff on it, then check the drive out and reformat to ext4 for reuse.  I'm pretty sure the problem is with the filesystem and not the drive. That's why I'm looking for a way to fix the filesystem before I reformated.

---

### Post by TheFu on 2021-06-12
FAT32 shouldn't be allowed to be larger than 64G by MSFT standards.  All sorts of inefficiencies start happening when those are larger than 32G.  

Of course, the limits added by MSFT in the 2000s was for good and bad reasons.  Good to prevent FAT-abuse. Bad because it forced everyone to buy a license to use exFAT instead.  exFAT is a much better file system, though on Linux, I'd choose f2fs instead for flash media.  f2fs supports full POSIX permissions while also reducing writes to flash storage.  In many situations, f2fs is faster than ext4 in popular benchmarks.

To deal with non-native Linux file systems, use the main OS where they are used.  For FAT32 and NTFS, than is Windows.

---

### Post by rsteinmetz70112 on 2021-06-14
OK, Thanks for the insight.

I've decided I'm going to copy all of the readable files onto another device and maybe that will give me a clue as to what is there and whether it is worth saving.
Then I'm going to try to recover the drive. Since I've tried the standard Windows utilities and they didn't work, I'm going to try a utility I found called testdisk which is available in the repositories and purports to be able to recover files from a FAT filesystem. If it trashes everything I'm no worse off than I am now and I'll give up, reformat and move on.

---

### Post by rsteinmetz70112 on 2021-07-12
OK after transferring most of the data to a new Hard Drive very slowly - some individual files seem corrupted. I think because they were originally larger that 4GB and Fat32 choked on them. All of the bad ones are the exact same size. 

I was able to use the program testdisk from the Ubuntu repositories to check the file system and when I switched it to a Windows Machine chkdsk /f worked and reported no problems. I tried converting the filesystem to NTFS in Windows but it keeps failing. It looks like it's due to the corrupted files.

SMART Tools report the drive has some bad blocks. I'm going to reformat to ext4 and see what happens then.

---

### Post by scorp123 on 2021-07-12
> **rsteinmetz70112 said:**
>  It looks like it's due to the corrupted files.

I'd say it's more likely that the files are corrupted because your disk is about to die?

> **rsteinmetz70112 said:**
>  SMART Tools report the drive has some bad blocks. 

There you go. And that number can only get bigger over time. So no matter what filesystem you put on that disk, files on it will start becoming corrupted again sooner or later.

---

### Post by TheFu on 2021-07-12
Bad blocks almost always mean a failing disk.  I'd stop using that drive for anything important, not even backups.

There are howto guides for using **badblocks** to force zeros into known bad blocks on a drive.  While my attempts to "restore" any bad block has always failed, it is fun to try.  Maybe you'll have better luck. The math involved can be really fun for trying to zero a block inside a partition, inside a PV, inside a VG, inside an LV.  ;)

Pro Tip: Don't use FAT32 unless there isn't any other choice.  

I have a hardware video recorder that only understands FAT32 or NTFS. Both of those are NOT file systems I'd choose, ever.  But the hardware limitation is what it is. No choice.  This recorder splits all files at 2GB sizes.  When I pull the files off the storage, the first thing I do is mux all those files back into a single file for the recording. That is typically between 10GB and 20GB size. Obviously, I'm not using FAT32.

---

### Post by QIII on 2021-07-12
When I start getting bad blocks, I take a disk out to 200 yards and do some hunting rifle practice.

---

### Post by scorp123 on 2021-07-13
> **QIII said:**
> When I start getting bad blocks, I take a disk out to 200 yards and do some hunting rifle practice.

Or you turn your old harddrives into a crossbow...
[https://www.youtube.com/watch?v=8iiMpVzPQFs]("https://www.youtube.com/watch?v=8iiMpVzPQFs")

Just for fun of course. Not to hurt anyone...

---

