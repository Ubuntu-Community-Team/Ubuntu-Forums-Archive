---
title: "SSD's, Swap, relatime and noatime"
date: 2016-02-27
forum: Hardware
---

### Post by irvine_himself2 on 2016-02-27
**Important, I don't need the disk space. My motivation is purely extending the life of the SSD memory.**
 
 **System specs:**
 16GB of physical RAM
 Partitions and storage devices:
    
[LIST]
[*]Swap: SSD: Linux-Swap … (16 GB) 
[*]Primary : SSD, EXT4 ……. (223 GB) 
[*]Backup1: external SSD: FAT32 
[*]Backup2: external HD:NTFS 
[/LIST]
 
 Running  **cat /proc/mounts**, **relatime** is enabled on all mounted media

 Running **cat /proc/sys/vm/swappiness**, I get the value of **10**

 Running** cat /proc/swaps**
 ```

Filename                        Type                           Size               Used             Priority
/dev/sda3                     partition                      16607228                0                 -1

``` Note, the above is slightly misleading, since it was checked just after a reboot. Previously, after laptop had been running for several hours, it was using about 4 MB.

 **Questions**

 **1/** It has been suggested that for a system with my specs, I would be better off replacing the 16 GB swap partition with a 512 MB swap file, ([see here]("https://askubuntu.com/questions/674320/what-ssd-optimization-are-needed-on-latest-ubuntu-version").)
 > Removing writes and expensive storage amount is the two factors why people *also remove swap area*. By default, Ubuntu creates swap partition equal to your RAM size. I have a 128 SSD and 6 GB of RAM. That means that by default Ubuntu will chop off 6 GB from 128GB, leaving 122GB for my OS, and 5% is typically reserved for root, so that leaves me 122-122*0.05=115.9 GB for myself. I might as well use that storage for something else, which is why I have only one main partition, no swap partition, but I do have a [512 MB swap file]("https://wiki.archlinux.org/index.php/Swap#Swap_file_creation") as a protective feature (not that I plan on running out of RAM, but it's always recommended to have swap)
 Note, I don't use hibernation and prefer to either either suspend to RAM or reboot completely.

**2/** If I replace the swap partition with a swap file, should I reduce the swappiness value, and, if so, what should this new value be?

 **3/** [This article]("https://sites.google.com/site/easylinuxtipsproject/ssd") suggest that you should leave about 7% of the available space, (max10 GB,) for **overprovisioning**.  
   
[LIST]
[*]What is **overprovisioning**  and how does it work? 
[*]The article is slightly dated, is still a good idea. 
[/LIST]

** 4/** I currently do not have a server or database application running, but, in the near future,I will most likely be installing Apache/MySQL on localhost to run MediaWiki, PHP and other interesting goodies.  Is **relatime** the best option for my situation, or would I be better off editing **fstab** to enable **noatime**?

 **5/** Checking **cron.weekly**, **TRIM** is set **TRUE** for all mounted media.  On the other hand, the above mentioned article suggests that I would be better off adding **fstrim** to **rc.local** so that it is run at each boot.  Does anybody have any views on this?

 **6/** Given the above, what is the best way to ensure the external FAT32 SSD is present, mounted and **TRIM**ed.

 **7/** Of academic interest: Would I have better off using the F2FS format for my primary partition?
 
 
 I am looking forward to hearing peoples opinions on the above. So thanks in advance
 
 Irvine

---

### Post by oldfred on 2016-02-28
I do not know answers, but can say what I do.

SSD life is now about the same as a HDD.
 SSD life test 2015 final
[http://techreport.com/review/27909/the-ssd-endurance-experiment-theyre-all-dead](http://techreport.com/review/27909/the-ssd-endurance-experiment-theyre-all-dead)
SSD life test: 2014
[http://techreport.com/review/26523/the-ssd-endurance-experiment-casualties-on-the-way-to-a-petabyte](http://techreport.com/review/26523/the-ssd-endurance-experiment-casualties-on-the-way-to-a-petabyte)

One reference I have used:
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

I turned off the weekly trim and run my own daily trim. But only have operating system and some other files that are well backed up. I would re-install if drive ever crashed.
I created my own trim like this, but also have a log:
[http://www.howtogeek.com/176978/](http://www.howtogeek.com/176978/)
Shows log also:
[http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html)

I use noatime but have no programs that conflict with that. They say relatime may be better then if worried about conflicts. I do use relatime instead of defaults for my data partitions on HDD.

I use gpt partitioning for all drives and most flash drives.

I use 2GB for swap, just to have some. Since I have 8GB of RAM, swap is never used.

If you are backing up to Windows formats, you are losing all ownership & permissions, as they do not support Linux type ownership & permissions. Originally I was running a compressed backup as a file to a FAT32 partition but noticed that backup was always 4GB? Turns out FAT32 max file size is 4GB. I now use rsync to other drives. And only Linux formats. EXT4 is my standard.

Not sure if you can even run trim on external drive. Somewhere I read that AHCI is required for trim and USB does not use AHCI. Some new drives for external use internally manage there own trim type functions. Also do not know if you can even run trim on Windows formats.

Over provisioning is leaving some space unused. I normally do not fully partition a drive when I first install anyway, so I currently have a lot of unused space. My SSD is 120GB and I have two / (root) partitions of 25GB and a ISO partition for booting ISO to install to HDD.

---

### Post by irvine_himself2 on 2016-02-28
Thanks **Oldfred**, it is always good to look at a problem with a different pair of eyes, and you have given me a lot to think about. In other words, I really need to plan out how to achieve my objectives, which are:  
   
[LIST]
[*]Extend the life of the SSDs 
[*]Have some method of reliable storage which is backed up. 
[/LIST]
 
 In my various graphics projects, I have worked with some very large HiRes NASA images and also batch processed video ranges with the Gimp for camera tracking and special effects using Blender. In addition, I have written some rules for “LanguageTool” and occasionally played around with subsets of Google's Ngram data. The idea being to use “Big Data” to find language rules. All of these projects work best with a lot of free disk space. As a result, I prefer to use external storage for files and data I am not currently working with.  

 Under Window's, I was in the habit of Using SyncToy to mirror Backup1 onto Backup2. After reading your post I think **rsync** may be the solution I have been looking for.. Finally, the reason for the strange choice of formats on the external drives is partly historical, but also seemed practical: When I want to download, (for example,) a collection Ngram archives,  I take Backup1 to  a friend with an unlimited data plan and leave it plugged into one of his spare Windows machines. I didn't realise thatFAT32 had a maximum file size, and will definitely be doing some reformatting!

 Thanks again for your response, it has been very helpful.
 
 Irvine

---

### Post by oldfred on 2016-02-28
If you want to share with someone who does not have Linux then you may need to use NTFS. It has journal and can store larger files.
You do lose ownership & permissions on your data, but if just data and not system you can easily restore valid set of ownernership & permissions. 
But if not using Windows best not to use Windows formats. They periodically need chkdsk which you can only run from Windows. Linux runs fsck on / partition every 40 or 60 reboots.

I use rsync, but another option.
 Discussion of issues on rsync bash file &  rdiff-backup  - TheFu
[http://ubuntuforums.org/showthread.php?t=2224428](http://ubuntuforums.org/showthread.php?t=2224428)
[http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/)
Sample rdiff file by TheFu
[http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880](http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880)
[http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use](http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use)

---

### Post by weatherman2 on 2016-02-28
I agree with oldfred.  I would not worry about taking unnecessary action anymore to "extend the life" of your SSD.  You may succeed in extending its life from 20 years to 30 years.  Will that matter?

I've been using the SSD in my netbook for about two hours, daily, for many hours a day.  After two years, S.M.A.R.T. reports that only 3% of the SSD's life has been used. (Presumably, spare sectors have been allocated to replaced failed sectors.)  But let's say my SSD is losing its life at about 2% per year.  If I have 96% life remaining now, then it will last for another 58 years or so, probably longer than I will last!

---

### Post by him610 on 2016-02-28
I was just reading about SSDs yesterday at the website referenced below. It seems to have some good advice.

[https://sites.google.com/site/easylinuxtipsproject/ssd]("https://sites.google.com/site/easylinuxtipsproject/ssd")

---

### Post by yoshii on 2016-02-29
I don't know much about this topic; I'm just here reading to learn.  
But it's worth mentioning that I have "noatime" enabled in my fstab to disable file last access time logging.  
I did it to reduce read/write input/output business.  Access time logging really isn't needed at all for a functioning system or for the user to know when a file was last modified or created.  It's a separate thing that is kind of redundant.  

I'm on Ubuntu Studio as a digital audio workstation.  In audio workstations, we need as much read/write efficiency as possible to ensure that recording and overdubbing and playing of multiple large audio files simultaneously goes smoothly.  Disabling access time logging is sometimes recommended to make file use less complex and more efficient.  

I would think that for flash media it would also be desireable to disable access time logging since flash media writes are not so simple.  Reducing the drive activity this way is an easy thing to implement and would probably be helpful if not harmless.  

That's my educated opinion on this.  Other than that, I'm just learning.  I did read somewhere in the past that ext4 file system has some provisions for SSD but I don't know much about it since I don't own any SSD drives.

---

### Post by irvine_himself2 on 2016-02-29
I am basically in the same situation as you. While, as a hobbyist, my main interest is in extending the life of the SSD on my nice, shiny, very expensive new laptop, I am frequently working with very large images, batch processing 'video ranges' and occasionally analysing 'big data'. This mean that efficient read/write access is a very a important side benefit, Unfortunately, although what you are saying is all true, it's not that simple, otherwise I would just enable 'noatime'. The basic problem is that there are many applications that need posix compliance to work properly. See [https://en.wikipedia.org/wiki/Relatime](https://en.wikipedia.org/wiki/Relatime).

Thanks for you input, it's good to hear what people use in real life applications of 'Ubuntu Studio' :D

Irvine

---

