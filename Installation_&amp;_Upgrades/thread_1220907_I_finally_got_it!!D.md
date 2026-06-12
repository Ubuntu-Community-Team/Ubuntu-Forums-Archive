---
title: "I finally got it!!:D"
date: 2009-07-23
forum: Installation &amp; Upgrades
---

### Post by TheNerdAL on 2009-07-23
I finally Got the Md5 Sums to be the same! After 2 Days and waiting almost 2 whole nights, I finally got it! I am new to Wubuntu. Also I created a Partition, and I would like to know if Ubuntu Creates one with that Partition Manager thingy when you first boot up. When I get to that Step, How Can I Tell Ubuntu to use that Partition?

EDIT: Also Thanks for Helping me if you helped me! I know I will love this Forum.:D

---

### Post by raymondh on 2009-07-23
> **TheNerdAL said:**
> I finally Got the Md5 Sums to be the same! After 2 Days and waiting almost 2 whole nights, I finally got it! I am new to Wubuntu. Also I created a Partition, and I would like to know if Ubuntu Creates one with that Partition Manager thingy when you first boot up. When I get to that Step, How Can I Tell Ubuntu to use that Partition?

EDIT: Also Thanks for Helping me if you helped me! I know I will love this Forum.:D

Am assuming you wish to dual-boot (as you are talking about partition/partitioning.

Boot into the liveCD.  When you get to step 4 (partitioning), you'll be presented with options on how to install.  Simplest is to use GUIDED RESIZE which will give you a graphical slider (you grab the hash-mark looking slider) and slide away to allocate the sizes per OS.  Another option is MANUAL.  You choose the partition you want to install Ubuntu, you format EXT3 or 4, you set mountpoint / (known as root), you define your SWAP and set as Linux SWAP file system, and continue with the install.

Post back if you need assistance in MANUAL installations.

Good luck.  BACK-UP before doing any partitioning work.  Also, if dual-booting with windows, DEFRAG windows first.

---

### Post by raymondh on 2009-07-23
OK/EDIT, just noticed that YOU CREATED A PARTITION already.

Is it primary or extended?  If primary, are you planning on creating a SWAP partition or not?

The general idea will be:

1.  Click to highlight the created partition
2.  Click EDIT (button below)
3.  Set to USE
4.  Format EXT 3 or 4
5.  Mountpoint "/" (or linux SWAP file system)

---

### Post by TheNerdAL on 2009-07-23
How Do I Find My Partition?

EDIT: Is a Swap File Necessary? And How do you do it?

---

### Post by raymondh on 2009-07-23
You ought to see it when/during the install.  

If you want help in identifying it prior to install, can you post a screenshot of gparted (syatem > administration > partition editor)?  

RE; SWAP.

If you have lots of RAM, not necessarily.  SWAP is an overflow of RAM should the program you are running is resource-intensive ... or if you habitually suspend/hibernate.

You can also [create a swap file]("http://ubuntuforums.org/showthread.php?t=1042946") instead of a swap partition.

Is a swap file more efficient than a SWAP partition?  I don't know.

---

### Post by running_rabbit07 on 2009-07-23
TheNerdAL, Raymond explains the process well, but I wanted to throw in a screenshot of my partition just so you know what you wanna look for.

From left to right you have my NTFS for windows, EXT3 / for the Ubuntu system and program files, EXT3 /home for file such as music, pics, and settings, and then lastly Swap which most people would note as being larger than it should be.

Hope this helps.

---

### Post by TheNerdAL on 2009-07-23
Thanks Guys, But I made the CD but when I boot up and click on the first option and hit enter, It Freezes and then says Error, This also happens When I hit "Check for CD Defects", or something like that. Please help?

---

### Post by running_rabbit07 on 2009-07-23
> **TheNerdAL said:**
> Thanks Guys, But I made the CD but when I boot up and click on the first option and hit enter, It Freezes and then says Error, This also happens When I hit "Check for CD Defects", or something like that. Please help?

Did you burn the disk at 4x or slower? If you burnt it faster it would mess it up.

---

### Post by TheNerdAL on 2009-07-23
> **running_rabbit07 said:**
> did you burn the disk at 4x or slower? If you burnt it faster it would mess it up.



Now you tell me?! Lol, what is a good speed?

---

### Post by running_rabbit07 on 2009-07-23
> **TheNerdAL said:**
> Now you tell me?! Lol, what is a good speed?

4x

---

### Post by TheNerdAL on 2009-07-23
> **running_rabbit07 said:**
> 4x

I would have loved it if Ubuntu told me in the directions. Thanks for your help.:) I will try it, hopefully I have more Blank CDs.:(

---

### Post by running_rabbit07 on 2009-07-23
> **TheNerdAL said:**
> I would have loved it if Ubuntu told me in the directions. Thanks for your help.:) I will try it, hopefully I have more Blank CDs.:(

It's in the documentation on their website, but even I didn't read it the first time. I got lucky though cause I was using a Rewritable CD that only burns at 4x.

---

### Post by TheNerdAL on 2009-07-23
> **running_rabbit07 said:**
> It's in the documentation on their website, but even I didn't read it the first time. I got lucky though cause I was using a Rewritable CD that only burns at 4x.

I am lucky We still Had Blank CDs. What could be another issue just in case?

---

### Post by raymondh on 2009-07-23
Personal files backed up?  Do so ... there are no guarantees (specially in HD work)

when able to finally boot the liveCD:

1.  Check CD for defects
2. If ok, select TRY UBUNTU WITHOUT CHANGES ... this will give you a live session ..... play around with it to see how your ubuntu version reacts well with your system specs (check wireless, keyboard functions, etc, etc.
3.  If satisfied, have a go in installing.

I know this sounds too precautionary and a hassle to do.  We are just trying to minimize hair-pulling adventures.

Remember, windows will have either FAT or NTFS file system.  Don't select that.  Your created partition (assuming you did not format) will be a unallocated space.

---

### Post by ezsit on 2009-07-23
> Did you burn the disk at 4x or slower? If you burnt it faster it would mess it up.

Burn speed was a factor years ago, like 1998, but these days and for the past several years I've been burning at 16X all the time and never have a bad burn. Is your hardware really ten years old that you need to burn at such slow speeds?

Back to the post. If you still have not successfully installed Ubuntu, go back and remove the partition you created for Ubuntu. Leave as much unallocated space on the drive as you can (at least 10GB for any useful installation). Boot from the Live CD and run the installer. When you get to the partitioning stage, let Ubuntu install to the largest free space and auto partition that space. It should work. Do not attempt this if you have less than 8GB -- it may work with less space but the system will be all but useless.

---

### Post by running_rabbit07 on 2009-07-23
> **ezsit said:**
> Burn speed was a factor years ago, like 1998, but these days and for the past several years I've been burning at 16X all the time and never have a bad burn. Is your hardware really ten years old that you need to burn at such slow speeds?.

 If you read the documentation you will see that it recommends burning at 4x. It quite obviously played a part in the fact his CD would not work. 

Is there a problem with people using equipment that is ten years old?

Thanks for the testimonial you should contact the guys who write the documentation and see if they will change it for you.

---

### Post by ezsit on 2009-07-24
> If you read the documentation you will see that it recommends burning at 4x.

I've read the docs, and burn speed used to be a common problem, one that has remained in the consciousness of many computer users far longer than the problem now warrants. I really don't care what the docs say about burn speed. Unless the burn speed is set above 12X, burn speed alone has very little to do with problems that are really media related, burner caused, dust related, or poor multitasking on the part of the operating system. 

CD burning at speeds above 12X are going to rely on buffer underrun protection mechanisms kicking in during the burn process. This is potentially where problems MIGHT occur. Buffer underrun protection will slow or stop the burn process to allow the buffer refill and not empty during the burn process. Stopping the burn process, even for a split second MAY, POSSIBLY, introduce micro gaps in the data recorded to the disc and cause problems when the disc is read. Keeping the burn speed to 12X or lower will prevent the buffer underrun protections from kicking in and should help IF the burner and your media are experiencing faults at higher speeds. Most burners and media can handle higher speed burning without issue.

Poor quality media and failing hardware are far more likely causes. Just because a second or third burn attempt at a slower speed proves successful, the speed of the burn really does not have much to do with the fact that an error did not occur on a subsequent write session. It is impossible to eliminate all other factors and blame burn speed for any and all errors. The coincidence of lower burning speed does not, in and of itself, rule out that media quality or dust was not the cause of the first bad burn.

Don't believe me? Try buying better cd media, use a newer burner, blow some canned air through the mechanism, and do not use the computer for anything else during the entire burn process while leaving the speed setting unchanged -- do all this and see if you don't get a successful burn the second time around. Then blame burn speed for the results. :-)

BTW,
> I got lucky though cause I was using a Rewritable CD that only burns at 4x.

You believe burn speed was the important factor the second time around? What else changed in the equation? The OP used a totally different TYPE of media the second time around. If you are going to run a test, at least compare apples to apples.

Also:
> I finally Got the Md5 Sums to be the same!
If the OP was correct and MD5 sums matched, then the first burn was fine. The fact that his computer booted successfully from one disc and not the other had nothing to do with burn speed. If the MD5 sums matched, then the burn, no matter what the speed, was cool.

PS
There is nothing wrong with using 10 year old equipment, just expect it to fail more often, that is all I am saying.

---

### Post by running_rabbit07 on 2009-07-24
> **ezsit said:**
> I've read the docs, and burn speed used to be a common problem, one that has remained in the consciousness of many computer users far longer than the problem now warrants. I really don't care what the docs say about burn speed. Unless the burn speed is set above 12X, burn speed alone has very little to do with problems that are really media related, burner caused, dust related, or poor multitasking on the part of the operating system. 

CD burning at speeds above 12X are going to rely on buffer underrun protection mechanisms kicking in during the burn process. This is potentially where problems MIGHT occur. Buffer underrun protection will slow or stop the burn process to allow the buffer refill and not empty during the burn process. Stopping the burn process, even for a split second MAY, POSSIBLY, introduce micro gaps in the data recorded to the disc and cause problems when the disc is read. Keeping the burn speed to 12X or lower will prevent the buffer underrun protections from kicking in and should help IF the burner and your media are experiencing faults at higher speeds. Most burners and media can handle higher speed burning without issue.

Poor quality media and failing hardware are far more likely causes. Just because a second or third burn attempt at a slower speed proves successful, the speed of the burn really does not have much to do with the fact that an error did not occur on a subsequent write session. It is impossible to eliminate all other factors and blame burn speed for any and all errors. The coincidence of lower burning speed does not, in and of itself, rule out that media quality or dust was not the cause of the first bad burn.

Don't believe me? Try buying better cd media, use a newer burner, blow some canned air through the mechanism, and do not use the computer for anything else during the entire burn process while leaving the speed setting unchanged -- do all this and see if you don't get a successful burn the second time around. Then blame burn speed for the results. :-)

BTW,


You believe burn speed was the important factor the second time around? What else changed in the equation? The OP used a totally different TYPE of media the second time around. If you are going to run a test, at least compare apples to apples.

Also:

If the OP was correct and MD5 sums matched, then the first burn was fine. The fact that his computer booted successfully from one disc and not the other had nothing to do with burn speed. If the MD5 sums matched, then the burn, no matter what the speed, was cool.

PS
There is nothing wrong with using 10 year old equipment, just expect it to fail more often, that is all I am saying.

The OP in this case has moved on and posted other threads fixing other problems, so apperently his install has been completed. 

Thank you for your advice.

PS, my system isn't that old and I have never had a bad burn from my drive.

---

