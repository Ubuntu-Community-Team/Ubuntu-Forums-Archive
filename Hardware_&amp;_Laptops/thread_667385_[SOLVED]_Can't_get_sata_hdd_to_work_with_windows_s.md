---
title: "[SOLVED] Can't get sata hdd to work with windows so I can dual boot with linux"
date: 2008-01-14
forum: Hardware &amp; Laptops
---

### Post by travismoore on 2008-01-14
I have an 80GB IDE HDD and am trying to get my new 500GB SATAII HDD to work. I have a sillicon image 3512 PCI card and the power cablesect. Its in my pc and in  the sillicon image control panel it appears to be working but it doesn't come up in my computer as another drive. I need it to work so i can back up my data on it and then put a fresh windows install and then linux. Il take some screenshots incase I'm missing something.

[http://img266.imageshack.us/img266/2009/problemas1.jpg]("http://img266.imageshack.us/img266/2009/problemas1.jpg")

P.S the pci card came with some linux drivers on the disc.

Any help is welcome,

Thanks,

Travis

---

### Post by travismoore on 2008-01-14
I don't quite follow what you mean. Like windows bios?

---

### Post by ARhere on 2008-01-14
A lot of the SIL image addon cards only recognize RAID sets.  Double check the documentation that came with the card to make sure it supports JBOD.  (Just a bunch of Disks)

If you don't know what that is, don't worry.  Just look for 'JBOD' in a phrase like, "...it supports RAID 0, 1, 1+0, and JBOD'.  If you don't see that, then you need a new add-on card.

We should verify first that your card will work before we get you to go mess with the BIOS.  Reply back with what you have discoved when you get the chance.  You can also post the SIL labs card model number and when I have time I can check it for you.

-AR

P.S.:  If you don't know what a BIOS is, I suggest you get a friend to help you.  We can try to help but messing up with the BIOS can make your PC unusable (*until you get an new flash chip or MB*), and you will blame Linux for it being broken. :(  No one wants that.

---

### Post by travismoore on 2008-01-14
On the box it says it supports **two independent** Serial ATA ports with data transfer rate up to 1.5GB/s
 
Also says: suppots co-exist RAID set and **non-RAID HDD**

Can't see anything anywhere about JBOD but do see about the RAID 0 and 1.

I do know what BIOS is I just didn't know what it had to do with a PCI card.

Thanks,

Travis

P.S: I would never blame linux. firstly because I haven't put it on my machine yet and secondly because its 10X better than windows =D

---

### Post by Rwild on 2008-01-14
Wow, you and I have the same problem.  I have put, literally, 50 hours into trying to figure out why my new SATA drive won't appear in Windows.  I went out and bought the same card you bought too.  Vista, will not, under no circumstance, view the disk as readable or writable.  A few times I got lucky, but then the drivers crapped out on me for some reason.  Try running the 7.10 live disk of Ubuntu and I bet you will be able to see your drive right off the get go.

---

### Post by travismoore on 2008-01-14
I'm on XP actually. My problem with that is I want to dual-boot my pc but i need to back up my files onto the 500GB first.

---

### Post by Rwild on 2008-01-14
I know... Have you run the live disk yet?

---

### Post by travismoore on 2008-01-14
Nope I haven't tried I've only burnt one off.

Oh just put it in I see so i can boot from the cd without affecting my windows?

---

### Post by Rwild on 2008-01-14
Try the live disk and see if you can view both of your drives.  If so, you can do the back-up right then and there.

---

### Post by travismoore on 2008-01-14
Thanks will have a try now =D

---

### Post by travismoore on 2008-01-14
Sorry if I seem a bit slow but i want to make sure I'm doing it right.

I have the disc in on start-up or just on windows?

and if it is on start up there are one of 6 options which do I click?

---

### Post by ARhere on 2008-01-14
Stupid question, but have you formatted the HDD yet?  If not, it will not appear in 'My Computer'.

Goto... Start->Control Panel->Administrative Tools->Computer Management.

A Computer management box will appear, click 'Disk Management' on the left bottom.

On the right, a graphical rep. of your physical drives will appear.  Look to see if your disk appears as 'Disk #' with a black bar and a title with something like, 'unallocated space' or something like that.

-AR

---

### Post by ARhere on 2008-01-14
> **travismoore said:**
> Sorry if I seem a bit slow but i want to make sure I'm doing it right.

I have the disc in on start-up or just on windows?

and if it is on start up there are one of 6 options which do I click?

Please try my last suggestion first.  When you boot the Live CD, it should be the first option.

-AR

EDIT:  I would rather you use a graphical system you are comfortable with for backing up important data!!!

---

### Post by Rwild on 2008-01-14
The first option is the way to go... Something like "Run and Install".  That will do the live boot on startup.

---

### Post by travismoore on 2008-01-14
> **ARhere said:**
> Stupid question, but have you formatted the HDD yet?  If not, it will not appear in 'My Computer'.

Goto... Start->Control Panel->Administrative Tools->Computer Management.

A Computer management box will appear, click 'Disk Management' on the left bottom.

On the right, a graphical rep. of your physical drives will appear.  Look to see if your disk appears as 'Disk #' with a black bar and a title with something like, 'unallocated space' or something like that.

-AR

Oh wow i feel pretty stupid now ... 


Its in there as "unallocated space"

Probably a stupid question but how do i format it ? and what file system would be best?

Thanks very much

---

### Post by Rwild on 2008-01-14
NTFS is compatible with just about everything these days so I can recommend that.  I also use FAT32 though.  You should be able to format it in computer management... I don't remember exactly how to in XP though... Sorry.

---

### Post by ARhere on 2008-01-14
> **travismoore said:**
> Oh wow i feel pretty stupid now ... 


Its in there as "unallocated space"

Probably a stupid question but how do i format it ? and what file system would be best?

Thanks very much

	](*,)  You had me really concerned there for a bit!  Ubuntu is **_FAR_** superior then Windows, but using it to back up important data when you are not familiar with it is a _bad_ idea.

Now that you have 'Disk Management' up, simply right click on the grey box that says "Disk #' and select 'create new partition' or 'format disk', whichever option presents itself.  A wizard will appear and guide you through it.  Just go ahead and format it as NTFS as ubuntu can see NTFS just fine.

**_WARNING:_  Make absolutely certain you select the correct hard drive or you can accidentally format the hard drive containing the data you wish to back up.**  If you left click on a drive letter/icon above, it will show you the drive it is on below.  Do not format those drives.

-AR

---

### Post by travismoore on 2008-01-14
Thanks guys, Sorry about the silly questions I just haven't installed a hard drive in years.

---

### Post by ARhere on 2008-01-14
> **Rwild said:**
> NTFS is compatible with just about everything these days so I can recommend that.  I also use FAT32 though.  You should be able to format it in computer management... I don't remember exactly how to in XP though... Sorry.

You cannot format a hard drive of his size using the default Windows tools for FAT32, even though the standard supports large drive sizes; you can in Ubuntu however, just use NTFS.

When you get your data backed up.  I suggest you turn your PC off and remove the HDD before booting Ubuntu.  The Live CD will not touch your hard drives, but if you choose to install it, you could accedently install Ubuntu on the backup drive.  Better safe then sorry.

-AR

---

### Post by travismoore on 2008-01-14
Can i just ask you quick if this linux set up would work.

I have an 80GB and a 500GB

I want to keep all the windows files on the 500GB and the ubuntu /home

Im gonig to have 40GB windows, 2 GB swap and 38GB Ext3 on the 80 GB

and I'm not sure how I am going to divide up the 500GB

I need to be able to move files onto the 500GB so i can access them from the windows and ubuntu partitions. As well as storing data from both OS's


Also for the install im gonig to back my files up to the 500GB then format the 80 and put fresh windows on it then put in the live CD and set it all up.

---

### Post by Rwild on 2008-01-14
I could be wrong on this, but I think with the 7.10 you won't have to divide the 500 at all.  You can keep that one for strictly storage and you should be able to view it in both XP and Ubuntu.

---

### Post by travismoore on 2008-01-14
> **Rwild said:**
> I could be wrong on this, but I think with the 7.10 you won't have to divide the 500 at all.  You can keep that one for strictly storage and you should be able to view it in both XP and Ubuntu.

But will i be able to keep the /home on it?

---

### Post by Rwild on 2008-01-14
Sorry, I'm not sure...

---

### Post by ARhere on 2008-01-14
This is what I suggest, but it is just my $0.02.

Divide up the 500GB Hard drive like so.
--------------------------
1.  155GB primary partition and format with NTFS <--use as your Windows Data drive
2.  160GB primary partition and format with NTFS <--use as your backup drive for windows data
3.  30GB logical drive ( to the 160 part) and format with FAT32 <-- easy file swap between all OS's
4.  155GB left free to be formatted as EXT3 and mounted as /home

Divide up the 80GB drive like this.
--------------------------
1.  40GB primary partition and install Windows here first.  Install ALL programs to the other 155GB NTFS disk.  This way you can blow your OS away and still have all your data for windows in your 155GB disk.
2.  2GB swap file
3.  38GB as '/'.  Remember during install to mount the other 155GB free space as your '/home'

I know it sounds like a lot, but this is 12 years of '*oh crap*' experience talking.  The point is, you want your application data on a separate partition/disk then your OS.  If you have to blow your OS away due to a screw up, all you data is safe.

The only difference, is you may want to divide up the 160GB partition and add 80GB to each 155GB partition, giving each OS a 235GB data disk.  You can use the NTFS 235GB partition to back up your windows data before beginning.  Makes it a little simpler.  So your 500GB drive will look like...
--------------------------
1.  235GB primary partition and format with NTFS <--use as your Windows Data drive, and windows backup
3.  30GB primary drive and format with FAT32 <-- easy file swap between all OS's
4.  235GB left free to be formatted as EXT3 and mounted as /home

Also, you want a REALLY easy way to back up all your data on your windows disk to another hard drive???  Just open up a command promt and type...
```
xcopy c: d: /h/i/c/k/e/r/y
```
The 'D:' should be your back up partition.  This will dump _everything_ while windows is running so you don't have to worry about finding what you need.

-AR

---

