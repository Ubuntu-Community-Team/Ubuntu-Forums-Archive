---
title: "Startup Disk Creator - Erased Wrong Disk"
date: 2010-10-30
forum: Hardware
---

### Post by parker8888 on 2010-10-30
While using the Startup Disk Creator, I accidentally selected the wrong disk to erase -- my 1TB external formatted in FAT32.  Once I realized what was happening, I pulled its USB cable mid-erase.

What I have now is unreadable.  In both Nautilus and Windows, I get files and or folders with nonsense names, dates, etc.  

The utility appeared to erase some data, but the majority of my data should (may?) still be there according to the figures in Nautilus.

Any ideas as to how I can fix this?

---

### Post by SpikeBzzz on 2011-02-07
Hi! Did you find the solution? 

I made the same mistake... Need help!

---

### Post by ronnielsen1 on 2011-02-07
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

> This ***recovery example*** guides you through TestDisk, step by step, to recover these 'lost' partitions by: 
 
[LIST]
[*] rewriting the corrupted NTFS boot sector, and
[*] recovering the accidentally deleted logical NTFS partition.
[/LIST]
 Recovery of a FAT32 partition (instead of an NTFS partition) can be accomplished by following exactly the same steps. Other [recovery examples]("http://www.cgsecurity.org/wiki/Data_Recovery_Examples") are also available. For Information about FAT12, FAT16, ext2/ext3, HFS+, ReiserFS and other partition types, read [Running the TestDisk Program]("http://www.cgsecurity.org/wiki/Running_TestDisk"). 


---

### Post by SpikeBzzz on 2011-02-07
Thank you.. I used it. 
The problem is that i don't have problem with partition.
So when I mount external hard drive all i get is a folder with strange files (not my 200 Gb of information). :( Baddd...

---

### Post by SpikeBzzz on 2011-02-07
Please, SOS.
I have no idea what and where should i look for a solution. How come that one can erase a harddrive disk from Startup disk Creator? What is this? The information is still on it (that's shown in "properties"), but I cannot see it...

---

### Post by ronnielsen1 on 2011-02-07
It's hard to troubleshoot without seeing what you're seeing. Can you give more details - screenshot - picture - better description?

---

### Post by IcarusR on 2011-02-08
If the data is critical I would recommend taking an image of the drive or cloning it to another drive. 
Then if you screw up when trying to recover data you still have the image to start again with.

Testdisk should help you recover your 'deleted' files.
Check out the instructions here

[http://www.cgsecurity.org/wiki/TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")

---

### Post by SpikeBzzz on 2011-02-11
Back again.. was busy, now continue to restore the data on my external harddrive. 

@ronnielsen1, 
I took a screenshot of what I see. 

[IMG]http://s43.radikal.ru/i102/1102/19/720da029039e.jpg[/IMG]

[IMG]http://s004.radikal.ru/i208/1102/0c/c865d9721393.jpg[/IMG]
[IMG]http://s47.radikal.ru/i115/1102/be/aeb78556243b.jpg[/IMG]

---

### Post by SpikeBzzz on 2011-02-11
@[IcarusR]("http://ubuntuforums.org/member.php?u=179763"), 
Will the image contain all the information that's not seen now?

---

### Post by komputes on 2011-02-11
I'm not sure that you can fix this, but you can surely salvage your information from the disk.

testdisk is a partition scanner and disk recovery tool. Running "sudo  testdisk" will scan your computer for media and offer you a menu-driven  way to recover your partition. 

Foremost is a console program to recover files based on their headers, footers, and internal data  structures. I have used foremost in the past. It will get you files from the disk and save them somewhere else, however you lose the file names.

More help could be found here:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Please mark the following usb-creator bug as still affecting you:
[https://bugs.launchpad.net/bugs/443330](https://bugs.launchpad.net/bugs/443330)

The bug was marked fixed in Lucid because the following comment was added to the changelog:

  * Provide a format confirmation dialog (LP: [#443330]("https://bugs.launchpad.net/bugs/443330")).

If this is not the case for you, please comment on the bug.

---

### Post by manoftao on 2012-11-08
Bloody Disk creator!!!!!!!!!!!!! Stupid idiots who designed the gui....... Yes, I erased my 2TB external by mistake.. Only afterwards, I realised the window is resizable... I had all music, video, backups and software/linux images stored there.... Damn. And I used this thing before, always struggling to click on the right drive... Bloody hell....

---

### Post by SuperFreak on 2012-11-08
Redundant backups of all data are a good way of preventing this

---

### Post by Iron Felix on 2013-03-19
> **SuperFreak said:**
> Redundant backups of all data are a good way of preventing this

Could you please recomend us the way to backup all data on a BACKUP drive.

---

### Post by Iron Felix on 2013-03-19
I deffenitelly choose the correct partion. But it wipes all of my external drives!

---

### Post by Kartist on 2013-06-01
Hi,
 
I am facing exactly the same issue. I accidentally erased a 2 TB harddisk while trying to create ubuntu startup disk on my 2Gb pendrive. Instead of erasing the 2 GB pendrive I think I erased the 2TB external hardisk using the Startup Disk Creator. I have lost 10 years of my life's work, critical files, projects and priceless family memories. I am a living dead if I can't get back my data. So please kindly share me your suggestions/solutions if you had managed to recover the data in your case. Your post is dated 2011, so I believe there should have been some technology improvements to undo this by now. 

It took only less than 5 seconds for the start up creator to erase my 2TB external harddisk. Also when I open the affected external 2TB drive there are no files visible, but the properties of the disk shows 1.5TB of the space as used, so I believe that the original data is somewhere in broken invisible formats inside the disk. That is my only hope. I don't have a alternate 2TB harddisk to take a backup or to perform testing. So I don't want to mess up further by choosing a wrong recovery method.

I have already gathered some ideas about testdisk and photorec. I didn't try them on the affected hard disk but I did try them on other portable drives for testing purpose, I tested them on a pendrive and retrieved files like a broken pieces from postmortem. If that is what the recovery tools can provide it will too impossible for me to rearrange and understand the data of size around 1.5 TB. Isn't there a way to just undo this and get back all my files?

I know I am foolish to have something that I considered worth more than my life in one single Hard disk. But it had been that way ever since I started computing and I never faced any issues. I was using windows and only recently I switched to ubuntu. And I made this mess while using ubuntu's in-built Startup disk creator.

Since you had faced the same issue 2 years back I hope I might get a useful advice from you on my situation. Please help!

-K

---

