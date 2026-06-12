---
title: "Hard Drive Recovery PLEASE HELP"
date: 2011-07-16
forum: Hardware
---

### Post by Postmaster_G on 2011-07-16
Ok, I really have a problem here. I have no idea why, but my hdd decided to die today?!? In my computer I have 2 hdd. One is for operating systems (ubuntu/win7/xp) and the other is for all of my stuff (I mean ALL of my pictures, music, documents, research... from over the years). 
It is this second drive that has died!!! Last time I did a backup was probably over a year ago, and after moving I have no idea where that drive currently is in storage (and I have taken many photos since then).
 
I really need to get this data! 
 
So here is where I am with it right now. I usually use win 7 because of program compatability. When I booted yesterday, it took a very long time to boot. After booting, my E drive did show up under "my computer", but it didn't have a name or display the space indicator below it. When I clicked on it, the explorer just hung and eventually I had to shut it down. 
 
Now running the UBUNTU 9.04 desktop live cd, it recognizes the drive and the name of the drive (the drive is actually called "stuff"), but it gave me two error windows and was unable to mount it. I tried to run the simple windows command that it listed, but that doesn't do me much good since that only runs on the boot disk (stupid windows arrg). I will try to upload a screenshot ASAP!
 
I have read through some of the forums, but it doesn't seem that there is a matching case (at least not that I have found yet). I am confident that the data is still on the disk... perhaps just the partition table or mbr or something is messed up??
 
Please help! I live for my music, and I currently have 0 of 80 gigs available to me. I spent countless hours ripping my disks, organizing, naming files etc. not to mention all of my pictures of family and friends. I really do not want to lose this "stuff".
 
Thank you all for reading this!
G
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=197625&stc=1&d=1310848984[/IMG]

---

### Post by Postmaster_G on 2011-07-16
I have just tried to run...

sudo ntfsfix /dev/sdb1 and got the following
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=197627&stc=1&d=1310852293[/IMG]

---

### Post by Postmaster_G on 2011-07-17
So... My drive is working again!  I am so happy!!!  After reading many other forum posts and whatnot online, I went ahead and tried to run chkdsk through windows.  I didn't think it was going to be able to work because the drive wouldn't mount the normal way.  I had to run the chkdsk three times, and each one took progressively longer.  The last run took over 4 or 5 hours [long enough to drive to the store, cook a steak and potatos, watch some of the show falling skies [which is ok], and suffer through the movie beastly [lol]]. 
 
I ran the command "chkdsk e: /f" without the quotation marks from an elevated command prompt from within windows.
 
I am not sure what all of this means...  the output from the last run will be posted below.  If anyone can comment or shed some light on what may have happend, I would appreciate it.  
 
The only reason I posted this problem here instead of on a windows forum is because...
1.  Linux users a problem solvers;
2.  Linux has a lot of powerful tools in general and I thought there may be something there to help me;
3.  I feel like the windows forum users would be like "well I guess you are going to have to format it" which was not an option or a good answer.
 
The only thing I can remember doing before the disk error is that I was running a "wipe free space" on that drive and stopped it about half way.  Other than that, it was just another day...
 
Let me know what you think!  I hope that someone will find this information useful in the future.
G
 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=197653&stc=1&d=1310892753[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=197654&stc=1&d=1310892753[/IMG]
:D:D:D:D

---

### Post by westie457 on 2011-07-17
Hi Glad you got it working again. Keep this link handy for future (if any) problems.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by Postmaster_G on 2011-07-27
So as it would turn out, my disk was pretty screwed!  I had shut it down after it 'started working' and when I rebooted, chkdsk ran again and the disk was not listed again.  I ran the command as admin like 3 more times [very time consuming], and was finally able to get 98-99% of my data copied to a new external drive.  I am currently reformatting the disk to see if it is even salvageable.
 
Any suggestions on how I could clean up the disk the best way after a failure like this?
 
thx

---

### Post by skatinjj on 2011-07-27
Well according to your screen shot in linux, there were I/O errors.  After recovering what you can, recycle the hard drive and get another.

Also, a disk is in pretty bad shape if Windows keeps running chkdsk on boot and it takes a *really* long time.

PS

Just my opinion of what to do with the drive, you don't have to get rid of it.  I personally wouldn't trust it after seeing I/O errors.

---

### Post by 23dornot23d on 2011-07-27
Not sure how to clean it up completely once something like that happens ..... chkdsk can only do so much and it seems if you have 98 to 99 % back you were very lucky this time.

But my advice now would be to go out and buy a 300 to 500 Gig USB HARD DRIVE ....... plus replace your main drive too .....

Backup regularly and keep at least two copies of important things like photos ....... so many people just have one copy ...... 

yet USB BACKUP DRIVES are so cheap nowadays. 

( unplug them and keep the data safe after the backup - I have 4 of these now and its almost impossible for me to loose everything - unless my house burns down - tempting fate here !!! )

Put smart monitor on too for the hard drive it lets you know when they are failing ...... question is why are your hard drives failing is it overheating ..... what is the airflow like around the computer ..... check for dust in air vents etc ...

---

### Post by Postmaster_G on 2011-07-27
> **skatinjj said:**
> Well according to your screen shot in linux, there were I/O errors. After recovering what you can, recycle the hard drive and get another.
 
Also, a disk is in pretty bad shape if Windows keeps running chkdsk on boot and it takes a *really* long time.
 
PS
 
Just my opinion of what to do with the drive, you don't have to get rid of it. I personally wouldn't trust it after seeing I/O errors.
 
I feel like you may be correct, I decided just to let winblows format the drive to NTFS [being too impatient to wait for a "dd" command with no progress bar]. That was last night at about 2am and here it is almost 4pm and it has only reached 30%! This drive may have to go... oh well, I would like a bigger drive anyway.
 
> **23dornot23d said:**
> Not sure how to clean it up completely once something like that happens ..... chkdsk can only do so much and it seems if you have 98 to 99 % back you were very lucky this time.

But my advice now would be to go out and buy a 300 to 500 Gig USB HARD DRIVE ....... plus replace your main drive too .....

Backup regularly and keep at least two copies of important things like photos ....... so many people just have one copy ...... 

yet USB BACKUP DRIVES are so cheap nowadays. 

( unplug them and keep the data safe after the backup - I have 4 of these now and its almost impossible for me to loose everything - unless my house burns down - tempting fate here !!! )

Put smart monitor on too for the hard drive it lets you know when they are failing ...... question is why are your hard drives failing is it overheating ..... what is the airflow like around the computer ..... check for dust in air vents etc ...
 
I do feel very lucky getting back what I did!  I could have lost everything.  I do have a backup drive in a storage unit somewhere, but that would still lose about a year of pics and music.  I am guessing by main drive you mean the one that is in my pc with all of my music/pics.  That one is going to be replaced [at least as of today I don't think I have any choice].  I still have another drive in there with my OSs.  I already have a backupdrive that I purchased the other day [250gb slim and small WD drive from Target for $30, awesome deal imho] to copy the recovery.  It does seem a bit nerving to have all of my stuff on that tiny drive [haha].  I don't think it is overheating, this drive that failed is the original hd that came with my pc in like '06/'07 and has gone through many hours of work, formatting, backup, etc... 
 
Is 5 years a decent life span for a drive that has been used quite a bit?
 
Thank you all for your input and advice.
G

---

### Post by swift100 on 2011-07-27
a narrow escape this time ;) backup is crucial, especially today when everything is cheap crap...

A good linux tool in such cases (and not only) is a distro called Parted Magic. It has a collection of disc utilities like the mention Test Disk (great utility for recovering lost partitions if the partition table decides to play tricks on you) or Clonezilla for good and fast disc / partition image backup / restore. A basic SMART reading app is there as well so you can check the health of the disc.

Here from what I've seen the SMART will not look good. Most probably the disc has lived up its life although considering not very gentle wiping of the free space maybe zeroing the disc out (total wipe out) will be just what it need. Playing with defragmentation tools is a risky business. My rule is - if it doesn't break don't fix it :D Wiping up free space is very seldom (if at any measure) necessary in my opinion.

And once again - get a backup drive and backup regularly! In windows this can be SyncBack, linux Grsync. SyncBack will do the job for you completely in Windows, Grsync will do similar in linux.

cheers!

---

### Post by 23dornot23d on 2011-07-28
Glad you got most of it sorted out ..... just got to love the little USB hard drives

cheapest storage (per MB) of data that I know of too ......... 

Mark the Thread as solved if thats ok now .... top right near the top of this page in [COLOR=Red]thread tools[/COLOR] in red ...

---

### Post by Postmaster_G on 2011-07-28
Well I am writing zeros to the drive now... using the WD Data Lifeguard for Windows to zero the drive as running the check for errors found bad sectors or something... At this point I am going to just see what happens. If the drive comes back with no errors after a format and scan I will be supprised. Then I will mark it solved regardless of the outcome, but will post the results. Thanks for all the advice. 
yeah I was worried I was gonna lose a lot!

---

