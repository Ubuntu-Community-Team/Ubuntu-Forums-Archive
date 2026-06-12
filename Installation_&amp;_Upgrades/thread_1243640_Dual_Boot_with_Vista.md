---
title: "Dual Boot with Vista"
date: 2009-08-18
forum: Installation &amp; Upgrades
---

### Post by bugsie on 2009-08-18
Hi again... Another question.

I want to install Ubuntu alongside Vista but I'm a little confused with regard to the instructions for doing so, in particular the bit about creating a partition. First a little about my current setup:

Two 250GB disks

Disk 0 partitioned as follows:[INDENT]C drive = primary 164GB currently Vista OS and programs.
G drive = logical 59GB empty.
E drive = primary 8GB recovery data.
[/INDENT]Disk 1 partitioned as follows:[INDENT]D drive = primary 232GB containing all my data.
[/INDENT]The instructions suggest that you can install Ubuntu without affecting current data and  talks about creating a new partition and formatting. It then warns that the entire disk will be formatted and all data lost.

I think it would be sensible to install Ubuntu in the G drive, including the swap area etc,  and create a second partition on the D drive for my data.

Is this sensible /  doable? What have I missed with regard to the aforementioned instructions about formatting and losing data?

Cheers

---

### Post by lisati on 2009-08-18
Sounds do-able. 

Be aware, however, that there have been reports of Ubuntu's partition editor causing problems Vista (I had it happen to me once but thankfully it was so easily fixed that I didn't make the connection at the time), so it will be a good idea to make sure your backups are up-to-date and to use Vista's partition manager if possible. 

If you haven't already done so, make a backup of your recovery partition to CD or DVD - if you're in luck there will be software preinstalled in Vista to help with the task.

---

### Post by ajgreeny on 2009-08-18
This all sounds more than doable, it sounds good to me.

The drive G which is empty is just crying out for ubuntu, and being linux the fact that it is logical is of no consequence; just try putting windows on a logical partition and see where you get!

You say that partition (drive G) is a logical one, which means it is enclosed in an extended partition which you don't comment on, however if it is empty and not actually part of the vista operating system, you should be able to put ubuntu on it without actually using gparted before you go into the installation of ubuntu.

When you get to the partitioning in the installation, choose Manual, find the empty 59GB partition and use that for the root and swap partitions by editing its partition setup.  I suggest a swap of about 2GB and the rest for root, though you could make root about 8 - 10 GB, and use the rest of the partition as /home.  Later on you will be able to set the second hard disk which I presume is ntfs, as a shared data partition for your windows and the new ubuntu install, and that way you will only have configuration information in your new home folder/partition, and not masses of duplicated data.

I do hope that all makes sense to you.  If not come back again with questions and let's see if it can all be made simpler for you.

---

### Post by bugsie on 2009-08-21
> **ajgreeny said:**
> You say that partition (drive G) is a logical one, which means it is enclosed in an extended partition which you don't comment on, however if it is empty and not actually part of the vista operating system, you should be able to put ubuntu on it without actually using gparted before you go into the installation of ubuntu.

Thanks for the feedback. With regard to the above point... I cannot find an extended partition in Windows Disk Management utility. The only reference I can find is to it being logical. Is this something I need to get to the bottom of before I can install Ubuntu?

Also... I got the impression from the instructions that partitioning as part of the installation is pivotal to the system realising that it is dual boot? I suspect I have got this wrong but want to be sure before I go ahead.

Thanks again for the help.

---

### Post by oldfred on 2009-08-21
As aj said the logical partitions are in an extended partition. There can only be 4 primary or 3 primary and one extended partition. The extended then can contain many additional partitions. Window only likes to be in primary partitions but Linux works just as well from extended partitions.

Additional info on partitions.
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by bugsie on 2009-08-21
So it looks as though I'm in business and can just install Ubuntu in my free logical partition. No need to partition at all and I assume the installer just formats the logical partition and not the entire disk?

With regard to the dual boot aspect... The Ubuntu install identifies the current boot paritition (i.e. in my case the primary parition where Vista resides) and installs GRUB in the this partition so my PC knows which OS's exist and where to go to get them?

---

### Post by Bartender on 2009-08-21
I'm guessing the Ubuntu installer will recognize your existing partitions on the first drive as: 

sda1 = Windows 
sda2 = recovery partition
sda5 = extended partition

If you just let Ubuntu auto-install to sda5, I think it will create sda6 as the main partition and sda7 as swap.  That's my guess.  

Your summary of the GRUB bootloader is pretty close.  As I understand it, GRUB installs a little piece of itself to the Vista MBR, which then points the PC to the rest of GRUB in the Ubuntu partition, which then points the PC to the default OS or the one you pick.

I hope that's close enough that I don't get slammed by some of the more knowledgeable guys...

---

### Post by bugsie on 2009-08-24
Thanks, Bartender.

If Ubuntu creates extra partitions, will I not exceed the total number allowed for a drive?

---

### Post by Bartender on 2009-08-24
Yeah, that's where a lot of people get hung up.

The theoretical limit for primary partitions is four.  I say "theoretical" because (in my admittedly limited experience) the Ubuntu installer can get cranky and unpredictable if you've already got three primary partitions.  Just try to build a fourth primary and you'll see what I mean.

So, the theoretical rule is 4 primary partitions and you're done.  My rule of thumb?  3 primary partitions can get you in trouble, so I always try to get down to 2 primary partitions.  

An extended partition allows you to detour around the "4 primary partition" roadblock.  

I don't know all the technical underpinnings but guess what we don't have to.  Think of an extended partition as a "box".  Once you've created the extended partition you can create several "logical" partitions inside the extended "box".  Your Ubuntu installation goes into those logical partitions.  It looks to me like the Ubuntu installer will by default attempt to create an extended partition, then build logical partitions inside the extended.  The installer recognizes the primary partitions as sda1 thru 4. That's why, even if there's only one primary partition, you'll see it skip sda2, 3, & 4 and create an sda5 (the extended partition), then create sda6 and sda7 for / and swap.   

Linux can start the computer from within an extended partition.  Windows cannot; it needs to boot from a primary.  If it weren't for Windows, you could just create one extended partition out of the entire drive and be done with it.

Windows can *access* data in a logical partition as long as the data is formatted NTFS or FAT.

That's a critical distinction so I'll repeat - Windows cannot start from a logical partition, but it can access data in a logical partition as long as the data is in a Windows-compatible format.

And this is where I'm starting to feel like a cat-herder because the topic goes off in too many directions.  So I'll stick to just one.  Let's say I want to set up a Windows/Linux dual-boot.  I have one HDD, but it's a huge 1TB drive so I've got room to do whatever I want.   I'm thinking about setting up a big data partition with video and music and photos that I could access from Windows or Linux.

In a perfect situation the first partition would be a primary partition, formatted as NTFS, for Windows.  Say 50GB.  Then I'd create one monstrous 950GB extended partition.  Within that extended partition I'd build a 20GB ext4 logical for the Linux / partition, another logical for the Linux swap partition, and a third ext4 logical for Linux /home.  /home would be - oh, I don't know - 30GB.

I'd still have around 890 GB left.  I haven't had any problems lately reading or writing to NTFS from Linux, so I'd probly just make one logical partition, formatted as NTFS, out of the entire free space.

Sometimes you can't get Windows down to one primary partition.  Sometimes you have a Windows Media Center partition, or proprietary partitions from the PC manufacturer.  But I'll always try to eliminate as many of those pesky primaries as possible.

---

### Post by bugsie on 2009-08-26
Hmmmm... That was not quite what I was expecting...

Tried editing the free logical partition space but ended up just reducing it to 8GB for a swap area leaving the remaining as "free" space. Had a couple of error messages about the kernel and not to add to a mount point, giving me a choice to ignore or cancel. I chose cancel after which the partition was shrunk before the error message was displayed again - I chose cancel again and quit the installation.

Back in Vista and drive G has disappeared altogether...

Not sure what happened... Should I have been creating new partitions in what is now free space?

---

### Post by Bartender on 2009-08-26
*Hmmmm... That was not quite what I was expecting...*

Not a good start to a post

*Tried editing the free logical partition space but ended up just reducing it to 8GB for a swap area leaving the remaining as "free" space. Had a couple of error messages about the kernel and not to add to a mount point, giving me a choice to ignore or cancel. I chose cancel after which the partition was shrunk before the error message was displayed again - I chose cancel again and quit the installation.*

Were you using the partitioner inside the Ubuntu LiveCD?  I don't use the Ubuntu partitioner.  I use [GParted LiveCD]("http://gparted.sourceforge.net/download.php").

Follow the link to the latest stable version.  Download the .iso.  Burn that download to a CD just like you did the Ubuntu install CD.  When you're done, you have a stand-alone partitioner disc.  Although the partitioner looks and acts the same as the one on the Ubuntu CD, it works better.

As far as I'm concerned, when it comes to partitioning the Ubuntu CD is easier to use when taking screenshots to post back here at the forums.  That's it.  Actually, it'd be great if you could post a screenie of what you've got now.

[Here's]("http://ubuntuforums.org/showthread.php?t=1249374") something I wrote up a few days ago that might help to get a feel for it.  There's also the GParted website, with forums, screenshots, some guides, etc.

If it were me, I'd boot from the GParted Live CD and "delete" all partitions inside the logical partition.  Here's where I'm hung up a little.  Is this 59 GB partition you refer to an extended partition, or is it a logical inside a larger extended?  In your first post you described it as "logical".  Did you mean a 59GB "extended" partition?  Because logicals exist within an extended partition and you didn't say anything about any other logical partitions.

I'm gonna guess you have a 60GB extended partition.  Next guess - using the GParted LiveCD you will be able to delete all partitions.

Then get out of GParted LiveCD, boot up the Ubuntu install CD, and I *think* you will have to choose the manual option and tell Ubuntu to install to the extended.  

You may be able to pick the guided, but I'm skeptical about that.  Manual install is really easy after you've figured out the "mount" thing, but if you don't understand that, it's hard to explain.  Maybe go to YouTube and watch a video or two...

Vista acts like partitions that aren't formatted in Windows file systems don't exist, so it's not surprising that Vista doesn't see it now.  That's not something to worry about.  If you'd installed Ubuntu successfully to that partition Vista wouldn't report it either.

Post a screenshot, OK?  It's easy.  Get to the Ubuntu LiveCD desktop, plug in a thumb drive.  Wait for it to be recognised on the desktop.  Go into Partition Editor.  When the partition map is up, go to Accessories>Screenshot, take the screenshot, save it to the thumb drive.  Then post back here and attach the screenshot.

---

### Post by Mark Phelps on 2009-08-26
> **Bartender said:**
> Vista acts like partitions that aren't formatted in Windows file systems don't exist, so it's not surprising that Vista doesn't see it now.

Actually, if the OP is using Vista's Disk Management utility, it will "see" the partition but since it's not a file system it understands, it won't assign a letter to it, nor will it let him do anything to it.

If Vista didn't even "see" that partition, that would be a much worse problem.

---

### Post by Bartender on 2009-08-26
Good point.  I was generalizing.  I just got called out in another thread for providing bad information; maybe I oughta call it a day

---

