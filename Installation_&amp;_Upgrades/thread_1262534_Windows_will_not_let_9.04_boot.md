---
title: "Windows will not let 9.04 boot"
date: 2009-09-10
forum: Installation &amp; Upgrades
---

### Post by justdrewid on 2009-09-10
So where I am at is this:  I have downloaded 9.04 less than 1 hr ago.  I have used nero 7 to burn a cd -r.  of the downoaded file.  
 
I am attempting to install onto a Dell Vostro 1500.  I insert the disk into the cd tray.  I turn off the system.  Turn on the system.  And Windows xp sp2 boots STILL.  Bios is configured to boot dvd before hdd.  
 
I re-installed xp just yesterday in preperation of this moment.  I have 3 Partitions: c: where xp resides 65gb     d: where I would like to install ubuntu 32bit.  partition size is 4gb      e: where I will try to install ubuntu 64bit partition is 6.4gb.
 
Does an .iso file need to be extracted vis-a-vis a tarball,  before attempting to install.  Will Nero 7 do an extraction?  
 
I am for certain that Microsoft is behind this, and would appreciate all educated feedback (as in EXPERIENCE (of the first hand)).   
 
My intent is to SHOW the people the beauty of ubuntu.  Please help me, help them, help you.

---

### Post by justdrewid on 2009-09-10
Is it possible for me to move this thread to the noobs forum?  I am alittle worried the response in this forum will be too technical.
 
BTW  How long do manners dictate I wait without any response before  repost my question?   Is there a quick way to repost a question? I figure wait till the next day for assistance, then repost.  Or 2 days?
 
Or should I repost till I get the attention of the moderators

---

### Post by bhaverkamp on 2009-09-10
Sounds like you just copied the ISO onto the CD/DVD? If so that is your problem. You need to burn an image and open the ISO as the image from your CD burning software. You can check this by viewing the CD from windows. Do you see a bunch of files or just the ISO?

---

### Post by justdrewid on 2009-09-10
Sounds to me, also,  like that is all I did. 
 
 So it therefore follows that I am a bit out-o'-wit. 
 
 BEFORE I burn the iso image to disk or AFTER I burn the image to disk I am to use my nero 7 to change it to a different file type?
 
Thanks for confirming my intuition.

---

### Post by ndefontenay on 2009-09-10
Hi.

Yes.

Using Nero, you should find an option Called "Burn Image". It will then prompt you to choose the *.iso file you want to burn to disk.

Also,

If you have formatted the drive you want to use for Linux with ntfs and called it D:, I suggest you erase it and keep it blank.

You will then have the option when installing to install on the unformatted disk space.

Happoy ubuntu install

Nico

---

### Post by justdrewid on 2009-09-10
I downloaded isobuster from their website and used the isobuster program to extract the .iso.   
 
So my plan is to take the extracted .iso file and burn ALL THOSE files to the disk.  Then I will be able to boot Ubuntu?!!??!?!

---

### Post by ottosykora on 2009-09-10
> **justdrewid said:**
> I downloaded isobuster from their website and used the isobuster program to extract the .iso.   
 
So my plan is to take the extracted .iso file and burn ALL THOSE files to the disk.  Then I will be able to boot Ubuntu?!!??!?!

no this is still not the right way, just burn the iso file to the DVD by using the option burn disk from an iso in your nero or other burning software. By this way there will be kind of boot sector copied to the DVD/CD. To copy files to the CD/DVD will not alone produce the 'boot sector' since this is something  you will normally not see when observing the disk in windows explorer or similar. The booting is then done by kind of hidden floppy image on the CD.

---

### Post by Bartender on 2009-09-10
It's very simple to check the CD - start up your Windows PC, pop the CD in the tray, and "Explore" the CD.  If you see one massive file, you copied the download.  That's wrong.
You want to see several folders and a handful of files.
There are several free utilities that are designed to burn .iso's.  ImgBurn comes to mind.

---

### Post by abhishek.malhotra35 on 2009-09-10
You can use poweriso to burn the iso image. The trial version is available on net.

---

### Post by presence1960 on 2009-09-10
read this right from our community documentation just made for people like you: those wishing to switch to ubuntu:

[https://help.ubuntu.com/9.04/switching/installing-burning.html](https://help.ubuntu.com/9.04/switching/installing-burning.html)

P.S. are you that paranoid that you really believe microsoft is conspiring to keep other install CDs/DVDs from booting? That is hysterical- LMAO

---

### Post by justdrewid on 2009-09-10
@ Ottosykora >>>  Simple enough "just burn the .iso to the dvd"  Straight forward and simple.  THANK YOU
 
@ Bartender >>>  "...and Explore"  Straight forward and simple.  Btw: I see one file- not multiple directories and/or files.
         I believe the Nero version that came w./ my dvd is the downgraded st it beversion and apparently does not handle .iso files.
          As I understand it after burning .iso to the dvd  I should see what you described, provided the burner program does its job.  
         Could I just use isobuster on the .iso file that was burned to the dvd??  Or must it be extracted by the burn program?
          Regardless of a reply to these queries, THANK YOU

---

### Post by justdrewid on 2009-09-10
@  Abhishek.Molotra35 >>> THANK YOU: for the image burner recommendation.  I have since my experience with nero 7  utilized: 
 CDBurner XP -reports say it does .iso burns but the burned file is still NOT extracted.
 AShampoo Burning Studio 6-  same problem, the files are not extracted.
 Something from last night @ 4am--said my dvd -r disks could not be copied to.
 
I am now to try Amarok.

---

### Post by justdrewid on 2009-09-10
PROBLEM RESOLVED


It seems that certain programs do not actually extract the .iso file.

My apologies to AShampoo, it seems their program does provided you (me!) utilize the proper format. 

So here I am on my Vostro 1500 with no apparent operability issues.


Thanks to those who provided their knowledge to me.  I hope to play it forward.  If I do not, then hold me accountable.


Here's to living a linux lifestyle.

---

