---
title: "Hard disk data recovery"
date: 2011-11-05
forum: Hardware
---

### Post by roopeshmicasa on 2011-11-05
**Hard Disk data recovery? Help!!!?**

                   Here is the problem in detail. 
I had hard disk with bunch of important files in it. My system had two  operating system (bad idea) Windows XP and Ubuntu 10.04. These both were  installed in a primary hard disk which was different from the one where  I used to store data (files) and this is the drive which I want to  recover as files have gone. Now, this hard drive is of 320 Gb capacity  so I divided it with 6 partions with NTFS file system so as to be  accessible in both the operating system.  

I had consistently having problem with the windows operating system,  therefore, after an advise from my friend I installed Ubuntu along side  windows. One day when I came back from college and started the windows  it was not running properly and I had to repair it altogether with  windows CD. Now, after that I was unable to access any of the logical  drive of the  secondary hard drive. I was seeing this message " Your  hard drive is not formatted. Format it now". Now I was panicked and  started reading on net for solution. Somewhere I found that Recuva can  be used to recover the data. So, after formatting all the logical drives  I used Recuva BUT it didn't help at all. 
I was so frustrated with this WINDOWS operating system that I altogether  washed it and started using Ubuntu and now all the drives are formatted  with ext4 file system. after sometime I thought I might can give one  more try to recover data so I used TEST DISK recovery. Although it  detected all the previous drives (partion), it is not able to detect any  file in it.  
If any one has any idea to recover data in this type of problem then please help. 

Please Help!!!!!!!!

---

### Post by diasf on 2011-11-05
A couple things:
1) For important stuff, one copy == lost. (Ubuntu One has up to 5Gb free storage on cloud!)
2) The problem could be on your system, not on the disk, you shouldn't have formatted it, but tried it on a different PC... if the problem was indeed on the disk, you should make an image of the disk on another HD and work with the image. If the disk is damaged, each access can corrupt more data.
3) Formatting the disks twice made things a hell of a lot more difficult. 

If the files were simple plain text, you could "cat" the disk and grab the pieces (I had to do that when I accidentally rm * on my c++ work folder) but for complex files that wouldn't work (pdfs, docs, etc).

There might be some tool able to recover them yet, but I do not know anything capable of dealing with all that, short of specialized recovery services, that can be quite expensive.

---

### Post by roopeshmicasa on 2011-11-07
> **diasf said:**
> A couple things:
1) For important stuff, one copy == lost. (Ubuntu One has up to 5Gb free storage on cloud!)
2) The problem could be on your system, not on the disk, you shouldn't have formatted it, but tried it on a different PC... if the problem was indeed on the disk, you should make an image of the disk on another HD and work with the image. If the disk is damaged, each access can corrupt more data.
3) Formatting the disks twice made things a hell of a lot more difficult. 

If the files were simple plain text, you could "cat" the disk and grab the pieces (I had to do that when I accidentally rm * on my c++ work folder) but for complex files that wouldn't work (pdfs, docs, etc).

There might be some tool able to recover them yet, but I do not know anything capable of dealing with all that, short of specialized recovery services, that can be quite expensive.

So, you are saying that it is now almost impossible to recover the data.
:(

---

### Post by mastablasta on 2011-11-07
yes that's what he is saying. that i would be very difficult to recover the data. You should have come to forums first. after windows repair was run you would need to update GRUB and then you could boot into Ubuntu and you would probably see the partitions (and could back them up). If not oyu oculd boot a live disk and use gparted to find parittions and possibly repair them if necessary.
 
Another option would be to use parittion doctor or similar windows programme to check for parititions and restore them if necessary. Formating the disk is a bad thing if you want to keep the data as it erases the data. Moreover, you formated the disk into a different file system. Windows probably told you that they need to be formatted because it couldn't recognise the ext4 parititions (it probabyl saw them as an unformatted drive). In any case if your second drive had only data on it it was still there when you repaired windows. but after you formatted it it was gone but was recoverably. but after you formated it to ext4 i think it is definatelly gone... unless maybe with some professional forensic tool....

---

### Post by roopeshmicasa on 2012-01-25
Thanks both of you for giving valuable suggestions.
Although I formatted my drives many times ......Hell ...I think more than 15 times ...I was able to recover my data :)
Also I like to share one thing that as you know I formatted it in NTFS, EXT4, FAT, EXT3, EXT2 ... Hell again ...every type of the file system. But still was able to recover it. 

The thing what I learned from above trouble is that even if you have formatted your drive many times and even in many file system type..but still you can recover it provided you have not overwritten it. 

I tried Recuva software in windows to get files from the drive. For that you must have your drive in FAT or NTFS type file system. You can recover files using deep scanning thing in the software. The only problem with this software is that the names of the file are changed that is it changes to some technical type of names like [000EFMOV] but it recovers the file. 

But...that's what I never wanted...File with different names and then have to rename....Imagine renaming thousands of files..Hell of work ..:)...I tried more search in google to find solution to this and then finally I found what I was looking for ...a software which works flawlessly.....TESTDISK ...I think this is the forensic thing you were referring to ..:)

I ran this program in Ubuntu and recovered everything as it is on the drive .....Only problem .....This program is terminal based and you have to know few commands before using it ...just few....and that's worth if you are getting all of your files after so much of trouble....TESTDISK rocks!!!!
Thanks to the person who made this program ....What a nice program to tell people about ...

Thanks everybody :)

---

