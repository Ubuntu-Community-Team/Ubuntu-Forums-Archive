---
title: "errno 5 input/output when installing 9.10 rc"
date: 2009-10-25
forum: Installation &amp; Upgrades
---

### Post by aaron_the_dude on 2009-10-25
Ok, i'm trying to install the release canidate of ubuntu 9.10 but I have been running into some problems.  I put in the disk, and when it is installing, it will get to 43 % finished and say errno 5 input/output error.  I tried cleaning the disk, and trying again, and i got the same error.  I tried putting ubuntu from the live disk to usb using the usb creater and installing it and got the errno 5 message at 43 % again.  I read up a post about faulty ram being the cause of it so I tried installing it with just one of the ram sticks at a time and that didn't solve any problems, same message.  What would you suggest I do?  I'm using the i386 live cd, and I haven't had so many problems installing 9.04 a few months ago.

---

### Post by atomicben on 2009-12-22
Bump...
 
I've followed these steps almost exactly.  
 
got 9.10 iso.
burned at 8x... still fails
tried at 4x.... still fails
tried installing a different cd drive and using the 4x disk...still fails
 
then I thought... maybe it was the hard drive... I removed my 40GB and tried all those steps again on my week old 500GB.  still fails....
 
installed ubuntu onto USB unetbootin-windows-377 (great program BTW). booted up to love CD...... still fails.
 
run memtest86+ on my 1GB of RAM and enabled my BIOS memtest.... passed all tests....  
right now i'm burning at 1x as a last ditch effort and I have ordered new RAM which won't get here until after xmas.  I'm so SOL.  I've been at this for HOURS.
 
 
the last thing I haven't tried is downloading another copy of the iso.  Seems pretty far fetched, but that's the next step.

---

### Post by atomicben on 2009-12-22
Solved.
 
Sure enough, downloading a new ISO did the trick.  I can't frigging believe it.  That's completely ridicilous.  I'm still stunned.  It's finally pat 23% and way beyond.  Moving FAST too.

---

### Post by ubuntgeek on 2010-04-22
I had the same problem. I had three hard drives that had, at one time or another, both Windows and Linux installed on them. At one point I could not install Linux 8 or 9, Freespire or Opensolaris on any of them. Changing CD drives didn't help nor did burning a new CD. Now here is the thing that really got me thinking. Windows XP would not install on the drives either, even after formating, and gave me an error message similar to the Linux distros. Here is what I did that worked for me:
 

 
[LIST=1]
[*]On one of the drives I booted up 	into Gpart and set a new partion table (that drive only had one 	partition) and then Ubuntu 8 installed no problem. This did not work 	for the other drives.  	
[*]For the second drive, I downloaded 	an utility from the manufacturer that was specific to that drive. It 	allowed me to “lowlevel” format it the drive (I think it was 	FAT32, but I don't remember). I used Gpart to set it as ext3. I 	haven't installed on this drive yet but I don't expect any problems. 	This is an old 8 gig drive that I want to use to mess around with 	Damn Small Linux.  	
[*]For the last drive, I used a Dell 	utilites CD I have and ran fdisk and deleted all the partitions and 	then formated FAT32.  I had no problem partitioning and installing 	XP on a NTSF partition and Freespire on the other. ( Actually I 	installed Freespire three times on the Linux partition because I was 	screwing around with it and messed it up a couple of times. Learned 	a lot though)
[/LIST]
 

 The only thing that I can conclude is that when I ran gpart to format a partition it wasn't really formating it completely. I don't understand much about MBR's and partition tables so I really don't know what was causing the problem but I just had this feeling that I was trying to write to a tablet that had a bunch of half erased words on it. So that is why I looked for programs that would really wipe the drive and it seems to have worked. So for me it was a hard drive issue but also software because I wasn't using the right program to wipe a drive clean before starting from scratch.  Oh, one last thing, one of those drive was one that Ubuntu 9 told me was failing with 9 bad sectors. I ran the diagnostics on it after formating and it is fine, that is the one I have partitioned XP/Freespire. Sorry for the long post.

---

### Post by schmickey on 2010-04-22
> **aaron_the_dude said:**
> Ok, i'm trying to install the release canidate of ubuntu 9.10 but I have been running into some problems.  I put in the disk, and when it is installing, it will get to 43 % finished and say errno 5 input/output error.  I tried cleaning the disk, and trying again, and i got the same error.  I tried putting ubuntu from the live disk to usb using the usb creater and installing it and got the errno 5 message at 43 % again.  I read up a post about faulty ram being the cause of it so I tried installing it with just one of the ram sticks at a time and that didn't solve any problems, same message.  What would you suggest I do?  I'm using the i386 live cd, and I haven't had so many problems installing 9.04 a few months ago.

Aaron:  I'm having the same problem with the Lucid RC. Sometimes I'll get as far as 56% and then halts with the I/O error.  I tried 2 different downloads of the .iso, two different flash drives.  Same problem.  My hardware is fine, Windows 7 runs fine.  No problems reported by Western Digital's drive diagnostics tools.  Karmic installed and ran just fine.  I hope whatever is causing this is fixed in the final release next week.

For now, I'm back to Karmic.  I guess I'll just leave this installation on the drive and do an in-place upgrade when the Final comes out.

---

### Post by ubuntgeek on 2010-04-23
> **aaron_the_dude said:**
> Ok, i'm trying to install the release canidate of ubuntu 9.10 but I have been running into some problems.  I put in the disk, and when it is installing, it will get to 43 % finished and say errno 5 input/output error.  I tried cleaning the disk, and trying again, and i got the same error.  I tried putting ubuntu from the live disk to usb using the usb creater and installing it and got the errno 5 message at 43 % again.  I read up a post about faulty ram being the cause of it so I tried installing it with just one of the ram sticks at a time and that didn't solve any problems, same message.  What would you suggest I do?  I'm using the i386 live cd, and I haven't had so many problems installing 9.04 a few months ago.

Aaron, this is the same problem I was having, (read my earlier post). I don't think it is a problem with the Ubuntu release or CD that you burned because I was getting the same error not matter what I tried to install on the HD (Including windows xp). Only after using Windows fdisk to delete the partition and then Windows format to format the partition DOS (FAT32 in this case) and then using Gpart to set up a Linux partition was I able to install Ubuntu. and Freespire, and XP on the Windows partition.

---

