---
title: "what format external HD compatible win/mac/linux"
date: 2008-07-22
forum: Hardware
---

### Post by trash on 2008-07-22
I just bought a Seagate FreeAgent external HD and was just wondering what format would be best for windows, mac and linux to use without partitioning(or maybe i should?)

---

### Post by DanubeRS on 2008-07-22
Most likely FAT, unless mac can read NTFS disks. FAT seems to be the 'portable standard' of removable media these days, therefore is compatible with almost all systems. Go for FAT if you want the compatibility, but if you're just gonna use windows and Linux use NTFS because of the faster file transfers.

---

### Post by trash on 2008-07-23
yup thought so, just wanted to double check incase compatibility had improved. Mac can read NTFS but cannot write without extra tools and I really want this drive to be accessible without any extra effort.

As far as transfer speeds, is there a big difference between NTFS and FAT?

---

### Post by Marie-Eve the Strange on 2009-11-07
(sorry for my bad english, i try my best)

Hi everyone,

I just got a laCie external harddrive 500Gb (Hi-Speed USB 2.0) and my objective is to make it work with Mac (macbook), Windows Vista and Ubuntu (dual boot). I don't know where is the best place to have help with that, so I'm trying here...

I'll explain what i've done so far. I've connected my HD on my MacBook, the installation process started and asked me how to format the partitions. It offered me to split the HD with a 32Gb Fat32 part for Windows and Linux. So I don't want to go any further in the process since I want the entire disk to be accessible from the 3 systems that I use and certainly don't want to have a partition with only 32Gb on it !

I've tried to find a solution by myself while searching the internet, I haven't found proper answer for my situation. I've written to laCie but it'll take 2-3 days before having an answer and I am not sure that they really can help me...

I'm working as a web programmer so I need my files to be tested on Mac, Windows and Linux without having to move my files all the time from a partition to another and I want to be able to read and write files from everywhere. Thats the point (for me) of having an external HD... And for backups, for sure.

I don't know very well how NTFS, FAT32 and FAT format work...

What is the easiest way to do what I want ? 

Thanks for your help !

(EDIT) a friend tells me to format my HD with Ubuntu in ext3 (that makes files accessible from Ubuntu and MAC) and install [http://www.fs-driver.org/](http://www.fs-driver.org/) on my windows for it to be able to read ext3 partition. Is it right ? Thanks !

---

### Post by Marie-Eve the Strange on 2009-11-07
I've found the solution ! I don't know the good or the bad of it, but it work well !

I've simply format (in Ubuntu with gparted) my harddrive to be in FAT32. I have access to it with Ubuntu, Windows Vista and Mac !

Thanks.

---

### Post by torkelhf on 2009-11-08
The major reason why windows users prefer NTFS is because FAT32 has a limit to the max file-size of about 4GB, which may be a problem if you run virtual OSs. 

But both filesystems are oldfashioned and slow compared to ext4, but for compatilbility mac/linux/win stick to FAT32.


Cheers,

T

---

