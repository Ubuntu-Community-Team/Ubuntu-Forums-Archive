---
title: "A Brief Question on External Hard Drives"
date: 2007-07-19
forum: Hardware &amp; Laptops
---

### Post by eljoeb on 2007-07-19
Heya,

I've already looked for this using the forum search and can't find a question quite like it (not saying its not there, just that I didn't see it).

I would like to know if I can use an external hard drive to put my CD's on, and share them between my Ubuntu and Windows partition.

Is this possible?  Are there any external hard drives you would recommend? 

Thank you,

Joe

---

### Post by paulphillips on 2007-07-19
Don't have any to recommend - never used one, however, assuming that they are mounted like any other harddrive, this should be possible.

You just need to format the external drive in a format that both Linux and Windows can read/write to: eg. FAT32, but there may be others.  Can windows read ext2/ext3 nowadays?

---

### Post by ukulele_ninja on 2007-07-19
I did this with my music actually and it worked fine.Just be careful of the format the files are in. Linux wont read WMA's.

---

### Post by arsenic23 on 2007-07-19
May I recomend buying a drive that suports eSata.

---

### Post by eljoeb on 2007-07-19
Thanks for the information and quick replies!  I'm not sure about eSATA... I don't think my computer could support it.  I do have an iLink (Firewire?) port... do external HD's support this or should I just use USB? 

> Linux wont read WMA's.

Not sure about this.  I saved all my music from windows as wma's and they seemed to work fine when I copied them over, after downloading something.  Not sure what it was.

---

### Post by arsenic23 on 2007-07-19
Almost every eSata drive also suports USB and/or firewire.  
As for firewire vs USB, I'd go for USB every time just in case you suddenly want to use it on another PC that lacks firewire in the future.


Also, if your board suports sata in general,  then it will suport eSata.  Most enclosures come with a bracket that converts one of your internal sata ports into an external eSata port.

---

### Post by LaRoza on 2007-07-19
I would recommend Firewire over USB if you are sure you will have Firewire availabe where you use it.

FAT32 is a safe format for both OS's, but it cannot hold files as big as 4 gigs, so if you have to store large files (iso of a dvd), you will need another file system. You could partition the drive also, if you want to use more than one file system.

---

### Post by Kowalski_GT-R on 2007-07-19
WD Mybook worked ok with Ubuntu from the very first time

[IMG]http://comtechnology.be/shop/images/902611ok.jpg[/IMG]


Be sure to have USB 2.0 or file transfer rate will be a nightmare.

I suggest firewire discs though..

ciao,

Andrea

---

### Post by pbcartwright on 2007-07-19
I have a 500Gb Mybook external USB drive that I use for both XP & Linux backups.
what I did first was to reformat it with a small fat32 partition for windows, with ext2ifs, then the rest is ext3.
I read this on a list I'm on:
>> Get rid of the fat32 partition, it's going to do more harm than good. Not only
>> because of the 4GB limit, but also because you need a good stable /journaling/
>> fs if you're going to be using this to backup your data. I like the idea of
>> two partitions, but for different reasons. As someone suggested on this list
>> awhile ago, have one very small fat32 partition that only holds the winders
>> drivers for the ext2/ext3 fs, and then just make the rest ext3. You really
>> don't even need the small partition if this will be for your own personal use
>> (I believe the person who suggested this needed to be able to share with
>> relatives), just install the drivers and you're done. Sure sounds better than
>> copying file-by-file *cringe*

---

