---
title: "Will a linux VFAT drive work in XP?"
date: 2008-09-30
forum: General Help
---

### Post by will0957 on 2008-09-30
Just as the topic states... i have a 1 TB external drive in VFAT format, wondering if it will work in XP. If not, is there any way to convert it to a format that will work in XP while not harming the contents?

Thanks

---

### Post by MrFSL on 2008-09-30
Windows XP has a hard limit set when formatting a drive fat32. This is 32 GB. However - I have found through personal experience that it can use a drive formatted in Linux fat32 - larger than 32 GB. 

Will a TB drive work - ... probably - but it shouldn't hurt it one way or the other to try.

Is there a way to format it without loosing the data? - ... I am going to say "no."  Even if tools existed to do this you would be formatting it NTFS (the only other file system that XP knows) and since NTFS is a Windows-proprietary product I would not see this as a safe process. --- Especially when you stand to loose up to 1 TB of data!

---

### Post by jpkotta on 2008-09-30
Why not just try it?  I seem to remember VFAT not working well with very large filesystems, but maybe I'm confusing that with older versions of FAT.  You can always copy the files to another filesystem.  In-place conversions of filesystems are usually not possible, and should never be trusted (i.e. back up your data before doing such a thing).

---

### Post by MrFSL on 2008-09-30
> **jpkotta said:**
> Why not just try it?  I seem to remember VFAT not working well with very large filesystems, but maybe I'm confusing that with older versions of FAT.  You can always copy the files to another filesystem.  In-place conversions of filesystems are usually not possible, and should never be trusted (i.e. back up your data before doing such a thing).

Yes - FAT (or FAT16 rather) has a limit of 2 GB.

---

### Post by TeXtonyx on 2008-09-30
Yes - FAT (or FAT16 rather) has a limit of 2 GB.

Fat32 has a 4GB filesize save limit. I tried to store a 24gig backup of another computer on a 
windows fat32 partition and it gave me an error message. I reformatted the drive with 
ntfs and it took the same 24gig file it just rejected.  

In windows you couldn't have a 1 terabyte fat32 drive. So there may not be the 4GB file
size save limitation. I would use Computer Management -> Disk Management in XP, and
look at the drives. If DM reports the drive as fat32, rather than the typical 'unknown' 
for Linux, I would assign a drive letter to it then, and it should work ok if it passes the
test of have a 4GB+ file written to it. An interesting question I think.

---

### Post by mixmaster on 2008-09-30
Why not use ntfs?

---

### Post by Nepherte on 2008-09-30
> **will0957 said:**
> Just as the topic states... i have a 1 TB external drive in VFAT format, wondering if it will work in XP. If not, is there any way to convert it to a format that will work in XP while not harming the contents?

Thanks
Fat32 is recognized by pretty much every operating system including the Windows family. That's why most hard disk manufacturers use this file system for their external hard disks. So to answer your question: yes, your 1TB external drive will work in XP and will be recognized as 1TB. However, as mentioned before, there is a 4GB file limit regardless of what operating system you use. So if you want to put files on it that are over 4GB, you might want to consider using another file system.

---

### Post by anaconda on 2008-09-30
> **will0957 said:**
> Just as the topic states... i have a 1 TB external drive in VFAT format, wondering if it will work in XP. If not, is there any way to convert it to a format that will work in XP while not harming the contents?

Thanks

the 4GB max file size in fat32 is too limiting.. nowdays it isn't THAT uncommon to have bigger than 4GB files....

What filesystem does your disk have now? if it is ext2/3 then it can be made to work in windows by installing the ext2 drivers to windows, Also the ntfs dirvers in ubuntu start to be reliable, so that would be another choice.

If you want to stick with fat32 then might I suggest that you would format part of the disk to fat32 and the rest to some better filesystem..

And yes bigger than 32gb fat32 partitions made in linux work in windows too.

---

### Post by will0957 on 2008-09-30
Thanks for the responses. The reason I can't just try it yet is because I don't have XP installed anywhere. I've got 1 machine, and it runs Ubuntu. I have my reasons, but I've been thinking about going back to XP either full-time or dual-booting. I've been running ubuntu for the last few years and love it, but some things I need to use it for are just less than ideal and require too much messing around (photo editing, gaming, etc).

That said, when I make the switch, I'm trying to figure out how I am going to get all my data from my 1 TB external drive to be able to be read in windows.

---

### Post by jms1989 on 2008-09-30
I have a 500GB FAT32 drive working under linux and windows. I also have two NTFS partitions for windows that have read and write access under linux and they seem to do ok, I don't use 'em much under linux as I have a larger ext3 partition to use but when I find a app that looks interesting under linux for windows, I'll save it directly to my windows desktop folder. So to answer your question, yes your 1TB fat drive will work just fine under linux and windows, just don't bother saving files over 4GB. If you are going to save files larger than 4GB, format it to NTFS or EXT3 (but install the ext3 drivers for windows to access it with read/write access). 

Now for formating it without damaging your data, I afraid thats technically impossible. Reformating will erase your data, so back it up if you plan to do so.

Cheers!

---

### Post by jms1989 on 2008-09-30
Deleted, duplicate post.

---

### Post by MrFSL on 2008-10-01
I would just like to point out that there is difference between maximum file size - and partition size.

---

