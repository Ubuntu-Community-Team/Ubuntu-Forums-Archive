---
title: "External HD Format: Fat32 vs. NTFS vs. ext3"
date: 2008-06-27
forum: Hardware
---

### Post by dbsoundman on 2008-06-27
Currently I have two external hard drives, one 80GB and one 200GB. I formatted both in FAT32 simply because I know that it is supported natively in linux and windows, but I'm wondering now if that is the best choice. I know that FAT32 fragments pretty easily, and I've found that if I have linux-based files on a FAT32 drive, like tar files, windows will not degfragment the drive. I would just format them as ext3 except that I would like to still be able to use these drives with Windows without having to add other programs on the windows machine. So, I was wondering if maybe something like NTFS would be better choice. The only problem I see with it is that I would need a program to make it work in Linux, but as long as it's dependable I suppose that could work. Does anyone have suggestions on what I could/should do here?

Thanks,
Dan

---

### Post by Odrodzona-Sarmacja on 2008-06-27
Imho fragmentation is not such bad thing. There are freeware tools to windows to defrag fat32 no matter what. Fat32 in general is safest file system yet for storing files, so personally I am sticking with it.

---

### Post by Archmage on 2008-06-27
Since FAT32 didn't support files over 2 GB, I would suggest changing the format.

NTFS isn't used native by Linux, but Ubuntu as an example can good read and write NTFS. But you need to run a long check if you unplug it to early. On the other hand it is a journaling filesystem that might help you if something goes wrong.

ext3 is nativly supported by Linux and is a journaling filesystem. But till now the Windowsdevloper weren't able to support it nativly in Windows, therefore you need a additonal 3rd-party driver and even than you can use only ext2 that is kompatible to ext3, but you miss the journal.

Please choose what you want, but I guess I would try NTFS in your shoes.

---

### Post by ukripper on 2008-06-27
> **dbsoundman said:**
> Currently I have two external hard drives, one 80GB and one 200GB. I formatted both in FAT32 simply because I know that it is supported natively in linux and windows, but I'm wondering now if that is the best choice. I know that FAT32 fragments pretty easily, and I've found that if I have linux-based files on a FAT32 drive, like tar files, windows will not degfragment the drive. I would just format them as ext3 except that I would like to still be able to use these drives with Windows without having to add other programs on the windows machine. So, I was wondering if maybe something like NTFS would be better choice. The only problem I see with it is that I would need a program to make it work in Linux, but as long as it's dependable I suppose that could work. Does anyone have suggestions on what I could/should do here?

Thanks,
Dan

Here NTFS is better choice for you, if you want to use it on the same computer with two different OS this is the best way to go. If you want to use from other windows machine then it won't matter (you can format in ext3 or ntfs) as then samba would do the job for you.

---

### Post by Odrodzona-Sarmacja on 2008-06-27
> **Archmage said:**
> Since FAT32 didn't support files over 2 GB

It doesn't? I have like 4gb files on my fat32 partitions...

---

### Post by ukripper on 2008-06-27
Fat32 doesn't support file bigger than 4GB and FAT supports only till 2GB

---

### Post by Odrodzona-Sarmacja on 2008-06-27
> **ukripper said:**
> Fat32 doesn't support file bigger than 4GB and FAT supports only till 2GB

I stand corrected. Highest time for Fat64 :D

---

### Post by ukripper on 2008-06-27
> **Odrodzona-Sarmacja said:**
> I stand corrected. Highest time for Fat64 :D

:lolflag: NTFS should be renamed FAT64

---

### Post by Odrodzona-Sarmacja on 2008-06-27
> **ukripper said:**
> :lolflag: NTFS should be renamed FAT64

Not after these horrible stories I heard about entire NTFS partitions vanishing out of sudden and inability to retrieve any data from them. Just horror. Certainly the windows programmers think of NTFS as of FAT32, but this is just not the same stable file system any more for file storage like FAT32 is, where you can get hard drive errors and partitions would die and you still got your data from them safely.

---

### Post by ukripper on 2008-06-27
> **Odrodzona-Sarmacja said:**
> Not after these horrible stories I heard about entire NTFS partitions vanishing out of sudden and inability to retrieve any data from them. Just horror. Certainly the windows programmers think of NTFS as of FAT32, but this is just not the same stable file system any more for file storage like FAT32 is, where you can get hard drive errors and partitions would die and you still got your data from them safely.

I tend to disagree on that one. I find NTFS pretty stable file system for Windows based machines which do get fragmented but not as much as FAT32. NTFS has very good features inbuilt, especially if you use windows XP pro you can do alot more than just basic things. Under Windows server PDC, Shared access and file permissions are pretty good using NTFS in Domain environment  using Active directory. But has it own outcomes such as closed source and can't be tweaked to your likings.

Bottom line is NTFS has more features and robustness when compared to FAT32 but still can't compete ext3 in stability and robustness, customisation and efficiency.

---

### Post by charliebrownau on 2008-10-30
FAT32 supports files up to 4 gig in size .
FAT32 can be formatted on drives up to 2TB in file size.

Some USB media caddy's require that you format PATA/IDE
drives to fat32 to support its TV Out function .

I have found its about the same for FAT32 and NTFS
that require Defragmentation .

I still use FAT32 in a few 80 and 120 gig drives
in my file server since I have found on those drives 
and the files on them (350 meg files) it reads quicker
using FAT32.

I have a USB Media Caddy which has a 160 gig PATA
drive formatted with FAT32 , it works well in 
computers with Linux , Windows 2000 , Mac , 
Windows 2003 and Windows XP . Everyone can write
and read fine to it .

In 2008 I would say that NTFS writing has finaly 
become stable with its recent work in NTFS for Linux.

I use EXT2 with my Linux install since I have a freeware
util that allows me to read and write EXT2 partitions
with Windows 2000 and Windows 2003.
When Linux is playing up its easier to reboot
surf the web with firefox and edit files with notepad
then have to use Nano at the command line under Linux.

---

