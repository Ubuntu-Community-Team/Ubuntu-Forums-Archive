---
title: "Partitioning a new 2TB HDD?"
date: 2012-11-30
forum: Hardware
---

### Post by cybrsaylr on 2012-11-30
A 3 yr old OEM Seagate HDD 1TB is failing. Replaced it with a new 2TB Seagate HDD......and hope it lasts longer than 3 yrs.

Wanted to clone over Windows 7 and Natty but that may not happen. W7 won't boot up anymore but Natty does on that failing OEM 1TB HDD that has a dual boot setup.

Anyways installed the new 2TB HDD, then partitioned it in half with GParted, 1TB NTFS and 1TB ext4. 
What confused me is at first it showed 3 partitions in GParted! 1TB primary NTFS, 1TB Extended 'unallocated' and 1TB ext4. Never saw this before. Usually see just 2 partitions not 3. Then I played around with Gparted and got it down to 2 partitions now showing just 1TB NFFS primary and 1TB extended ext4. Is this correct and will I have any problems if attempting to dual boot again with W7 and Ubuntu on the NTFS side? Plan to use the other ext4 partition for storage.

---

### Post by dannyboy79 on 2012-11-30
i don't think ubuntu will run on NTFS, or at least I wouldn't do it that way. I would just use windows 7 disk to install win 7 on a 500gb partition. after that's done, i would then pop in an ubuntu disc and put it on a 500gb partition. during it's install it should add win 7 to it's grub menu. then within ubuntu create an extended partition and then a 1TB ext4 partition for storage.

---

### Post by cybrsaylr on 2012-11-30
dannyboy79, 
I know Ubuntu won't run on NTFS and that is pretty much what I planned on doing if I couldn't clone over everything. Before the OEM drive failed I had a triple boot system of W7, Natty and Precise which ran great. Did a lot of tweaking to Natty and it ran great. Hated to lose all that Natty customizing I did....lol

What really threw me was seeing those 3, 1TB partitions on the new 2 TB drive. First time I ever saw that.

---

### Post by dannyboy79 on 2012-11-30
you could use partimage I am sure to clone your natty install if you really want it.

---

### Post by ahallubuntu on 2012-11-30
> **cybrsaylr said:**
> Anyways installed the new 2TB HDD, then partitioned it in half with GParted, 1TB NTFS and 1TB ext4. 
What confused me is at first it showed 3 partitions in GParted! 1TB primary NTFS, 1TB Extended 'unallocated' and 1TB ext4. Never saw this before. Usually see just 2 partitions not 3.

It's helpful to understand what the different type of DOS partitions mean (yes, you are using an ancient standard for partitioning PC hard drives, only recently superseded by UEFI).

By DOS standards every hard drive can have up to four "primary" partitions.  At some point, people wanted more than four partitions.  A hack was created called an "extended" partition - basically, a container partition.  You were still stuck with four primary partitions but one of them could be an "extended" type that could have many "logical" partitions created inside of it. 

Windows probably ought to be installed in a primary partition, but don't be afraid of logical partitions for Linux.  It gives you more flexibility later to have more than four partitions someday, and you really lose nothing by using them.  An "extended" partition really takes no space (or nothing significant, a few bytes for housekeeping).  It's just a container for logical partitions.

My personal preference nowadays is to make small partitions for the operating systems and a large shared data partition.  On a 2TB drive, I'd probably make a primary partition for Windows 7 (perhaps it will want a small boot partition too - make that a primary) of say 120GB, make the rest of the drive an extended partition and make say 40GB for Ubuntu (ext4) and a big NTFS partition that can be shared by both.  In Windows, you can move "My Documents" to what will become the E: in Windows so the C: is only for software and Windows.

So I'd probably do this: use Gparted to create about 1800GB extended partition at the end of the drive, about 150GB (or less) free space at the beginning.  Install Windows 7 first (cloning probably won't work with the errors you have) into the free 200GB space, let it make whatever partitions it likes there.

Then make the rest of the partitions in the 1800GB: a smaller Ubuntu partition, a swap, and a very large NTFS partition.

If there are no errors on the Ubuntu partition on your old drive, you can clone it (after installing Win7) with Gparted, which can copy partitions from drive to drive.  You'll have to re-install/update grub with a live CD plus create a new swap partition and update your /etc/fstab to point to the new UUIDs of the new partitions you created on the new drive.

---

### Post by cybrsaylr on 2012-11-30
> **dannyboy79 said:**
> you could use partimage I am sure to clone your natty install if you really want it.

Thanks for the tip on partimage.
Didn't know what to use to clone Ubuntu.

---

### Post by cybrsaylr on 2012-11-30
> **ahallubuntu said:**
> My personal preference nowadays is to make small partitions for the operating systems and a large shared data partition.  On a 2TB drive, I'd probably make a primary partition for Windows 7 (perhaps it will want a small boot partition too - make that a primary) of say 120GB, make the rest of the drive an extended partition and make say 40GB for Ubuntu (ext4) and a big NTFS partition that can be shared by both.  In Windows, you can move "My Documents" to what will become the E: in Windows so the C: is only for software and Windows.

So I'd probably do this: use Gparted to create about 1800GB extended partition at the end of the drive, about 150GB (or less) free space at the beginning.  Install Windows 7 first (cloning probably won't work with the errors you have) into the free 200GB space, let it make whatever partitions it likes there.

If there are no errors on the Ubuntu partition on your old drive, you can clone it (after installing Win7) with Gparted, which can copy partitions from drive to drive.  You'll have to re-install/update grub with a live CD plus create a new swap partition and update your /etc/fstab to point to the new UUIDs of the new partitions you created on the new drive.

Thanks for the tips. They are very helpful.
Was wondering about how to best split up the new drive.

When I got warnings the 3 yr old OEM drive was failing I got a 128GB SSD and put 12.04 on it as a boot drive. At first I was going to dual boot it with W7 and 12.04 but decided not to because W7 would eat up too much space on that SSD, plus I never really used W7 much in the past 3 years. The main use of the W7 500 GB NTFS partition in that failing OEM 1 TB drive was storage for Ubuntu....lol.  So I decided to just install 12.04 on the SSD. It runs great, blazing fast and boots up 12.04 in 20 seconds. 

I then disconnected the 1TB OEM drive to conserve what life was left in it. However the few times I used it I had no problems booting up into either W7, Natty or Precise.

Then I finally got the new 2TB HDD and at this point am trying to decide how to best use it for W7 and Ubuntu. All my PCs are dual boots. Can't see getting a new PC and then just dumping Windows which I paid for, even though at this point in time Windows is seldom used anymore.

---

### Post by cybrsaylr on 2012-12-02
> **ahallubuntu said:**
> My personal preference nowadays is to make small partitions for the operating systems and a large shared data partition.  On a 2TB drive, I'd probably make a primary partition for Windows 7 (perhaps it will want a small boot partition too - make that a primary) of say 120GB, make the rest of the drive an extended partition and make say 40GB for Ubuntu (ext4) and a big NTFS partition that can be shared by both.  In Windows, you can move "My Documents" to what will become the E: in Windows so the C: is only for software and Windows.
I've read of this....
In Windows, you can move "My Documents" to what will become the E: in Windows so the C: is only for software and Windows. 

And on a related note to save wear and tear on my SSD with Ubuntu, is it a good idea to do something similar and simple move the entire "Home Folder" off the SSD to a partition on the 2TB HDD?

---

### Post by ahallubuntu on 2012-12-02
I wouldn't worry about "wear" on a modern SSD myself.  They are much more robust than in the past.  I would still make regular backups whether it's an SSD or a regular hard drive, though. But by the time it "wears out," the cost to replace it will be a fraction of what you paid.

SSD prices seem to have fallen by about half in just the last year.  I got an Intel 120GB SSD for $90 a few weeks ago.  A 240GB Intel SSD was on sale for about $140 over Black Friday.  In five years, I'll bet your SSD will cost very little if you need to replace it (but I'll bet it won't have "worn out" yet).

---

### Post by cybrsaylr on 2012-12-02
Indeed prices are dropping on SSDs.

Got my 128GB Kingston SSD in the beginning of this past October on sale and paid only $80 for it! 
It has been amazing compared to the failing 1TB OEM HDD it replaced.

Also saw some terrific Black Friday deals on SSDs and that is when I got this new 2TB Seagate HDD for $70 at Newegg.com for storage. Just hope it lasts.....lol

SSDs are making all kinds of fantastic claims about how long they will last but am hearing that even the newest SSDs coming out are burning out after a couple or more years. So who knows......:confused:

---

### Post by dannyboy79 on 2012-12-03
i've been leary about puchasing seagate drives ever since the fireware bug where it doesn't wake from sleep/suspend correctly and results in data corruption randomly. hopefully you didn't get a 2TB with the following firmware. [http://www.cnet.com.au/seagate-offers-fix-for-faulty-7200-11-hard-drives-339294514.htm](http://www.cnet.com.au/seagate-offers-fix-for-faulty-7200-11-hard-drives-339294514.htm)

---

### Post by cybrsaylr on 2012-12-03
dannyboy79,
Hopefully things have been corrected since your above article was posted.

I switched to Seagate years ago when they went to the 5 yr warranty. WD only offered 3 yrs. Never had any problems with the old IDE drives that were built like tanks. The new SATA drives are not built as sturdy whether they be Seagate, WD, or others makes that apparently are all made in Thailand now! All SATA drives 1TB and bigger seem to have failure rates higher than in the past. And all companies only offer a 1 or 2 year warranty now which seems to reinforce the belief large SATA drives 1TB and larger, are now not made as well as in the past. 

My failing 3 yr old OEM 1TB Seagate HDD is the first drive failure I had in 14 yrs. Luckily I backed it up and lost nothing important.

---

### Post by cybrsaylr on 2012-12-07
OK, here's what I ended up doing.

Have 2 drives in PC and running. Hope what I did is OK and won't cause any problems down the road.
When PC boots up 12.04 starts right up on the SSD, takes 20 seconds.
If I want to boot into Windows 7, I have to hit 'F12' after hitting to power button and select, 2TB HDD to boot up.

The 128GB SSD has 12.04 installed along with a 8GB swap partition.
The 2TB HDD was partitioned in half with Windows 7 on first 1TB partiton and the other 1TB was partitioned as Ext4 for storage. 

Ran into something weird here. Used GParted to partition the 2TB HDD. For some reason I could drag & drop files into the W7 NTFS partition but NOT into the Ext4 side! It was like I was locked out of the Ext4 side, said permissions were denied! 

Solved it by right clicking on the Ext4 partition in the left side launch bar and clicked on Format, This reformatted the Ext4 to Ext4 again but now renamed it as a 'New Volume'. Then as a New Volume I was able to drag and drop files into this 1TB Ext4 partition as desired. Anyone have any idea why this happened? Usually had no problems in the past but this was the first time I was blocked from dragging and dropping files into any partitions. At this point I can drag & drop files into either of the 2 partitions created for extra storage as needed. This gives me all the storage space needed. Just hope it is OK and won't cause problems down the line.

---

### Post by oldfred on 2012-12-07
I think you want to permanently mount the ext4 partition.

       Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

    
example:
       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6
For ntfs UUID shown is example only see below:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

   For ext4:
UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /media/Data ext4 defaults,noatime 0 2

   ** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD
and/or 
sudo mkdir /media/Data
** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab

   ** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if prevously mounted:
sudo mount -a

---

### Post by cybrsaylr on 2012-12-07
WOW!!!
Thanks for the links oldfred.
You know, I've been using Linux since the beginning of 2007 but never got into that 'part' of Linux. 
Read through all your links and they are pretty much all Greek to me :redface:
Will have to be doing a lot on studying to make sense of all that.

Whenever I needed an extra HDD in the past they were all ext-HDDs and you just had to plug them in with a usb cable and any partitioning needed was done with Seagate DiscWizard. This is the first time I actually added a HDD to my PC and partitioned with just Linux apps. 

So the big question is will there be problems down the road with the way I set things up in post #13?

---

### Post by oldfred on 2012-12-07
I am not sure why you had to reformat. And you never should just to reset ownership nor permissions as you can use commands to change settings.

But settings for entire partition are controlled by mount in fstab if NTFS. Or if Linux you mount with Linux defaults and control ownership & permissions.

External drives often are NTFS or FAT32 so the default mounts often just work. But if Linux or internal drives you really need to control settings.

Morbius1 method is not all that difficult as it is copy & paste into fstab with some edit for your specific UUID and whatever mount point you may want to give it. His examples also just work if you like the mounts he has used.

---

### Post by cybrsaylr on 2012-12-08
> **oldfred said:**
> I am not sure why you had to reformat. And you never should just to reset ownership nor permissions as you can use commands to change settings.
As I said I was new to this.
Used GParted to format to Ext4 and that partition first let me move some files to it but then blocked all movement a day later. Don't know why and didn't do anything to change things. Then the next day I noticed the few files I had moved to the Ext4 partition were moved mysteriously somehow to the NTFS partition with Windows 7! This was when I discovered Ext4 partition was 'frozen' not allowing anything to be added to it. 
That was when I experimented by right clicking on the **2.0TB Hard Disk 1.0TB Filesysyem** in computer which opened up an icon on the left side launchbar for that Ext4 partition. I then opened it in the launchbar with a right click and did a reformat which changed its name from **2.0TB Hard Disk 1.0TB Filesysyem** to **2.0TB Hard Disk New Volume**, which allowed files to now be drag & dropped into this 'New Volume'.

I just stumbled upon this 'solution' by trial and error, not knowing about all that fstab stuff....

---

