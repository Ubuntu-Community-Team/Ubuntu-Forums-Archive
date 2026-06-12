---
title: "Help manualy partition"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by rreyes1316 on 2009-04-29
As a newbie I am just starting to grasp the Ubuntu environment. I dual booted, tested ubuntu, created a remastersys iso, and tested it out on another drive--I am now ready to reinstall on my WD Raptor 150. But how do I install on an ext4? I used gParted and formated my test drive to ext4. When I went to reinstall my remastersys image I could not figure out the Manual partition nor understand how to set a root or swap partition. I was completely confused. When I defaulted to Chose "Use entire disk" it created an ext3 and installed everything on that instead.

Can I get a "hand-over-hand" guidance for this "Ubuntu Dummy".

Thanks

---

### Post by udippel on 2009-04-29
> **rreyes1316 said:**
> As a newbie I am just starting to grasp the Ubuntu environment. 
[...]
I was completely confused. When I defaulted to Chose "Use entire disk" it created an ext3 and installed everything on that instead.

Can I get a "hand-over-hand" guidance for this "Ubuntu Dummy".


You don't sound like a 'dummy newbie', though!?

Actually, I don't know what you mean with 'remastersys iso'; so you can make out who the dummy actually is.  ;)
But I managed to install ext4 easily, even with the Desktop version. In that step where the real dummies select 'whole disk', you need to click the lowermost tiny box for manual partitioning; and then you can set all partitions, mount points, and partition types (including ext4).

Uwe

---

### Post by rreyes3000 on 2009-04-29
That is where I got confused. I was confused with the set partition step and the mount points. There was a drop down menu that gave me all sorts of file system options. I selected ext4 then went to the next step. This when I got a window that stated I needed to set a swap partition.  Actually, I have been working with ubuntu for about two weeks and my exact memory of what I encountered is hazed. I have so much new info floating around my membrane and going insane:P  So . . . is the window that pops up used to setup my swap partition? Do I use 1.5 times the amount of ram I have? By doing so, is the rest of the drive I formated to ext4 left as is and then the OS installed on it?

Told you I was confussed?!

---

### Post by -kg- on 2009-04-29
Apparently you wanted to use the entire disk for your installation, so this should pretty well be an easy install.

If I'm not mistaken, the only way to use the ext4 file system is the Manual Partitioning selection.  The installer does not default to ext4; you have to choose it at partitioning time.

The quickest way to use ext4 as your file system is to reinstall using the Manual  Partitioning option.  I've just done it 3 times today (Ubuntu, Kubuntu, and Xubuntu) using the Manual partitioning option, so it's pretty fresh in my mind.

Once you get to the partitioning screen after having selected Manual Partitioning, you will be presented with a Graphic representation of your hard drive(s) with a list of the partitions and free space (if any) below it.  The only way that I found to select the partition or free space that you want to perform operations on is to highlight the line in the list below the Graphic.  In my case, I prepared some free space using the [GPartEd Live CD.]("http://gparted.sourceforge.net/")

The following assumes that you only have one internal hard drive installed.  If you have more than one physical hard drive installed, you need to make sure you select the following partitions on the correct hard drive; i.e., if you have Windows on sda and your Ubuntu installation is on sdb, make sure you perform these operations on sdb.

Since you have installed using the Whole Disk option, your disk is likely formatted into two partitions; a root (/) and a small swap partition.  Probably the easiest way to go is to delete the ext3 partition by highlighting the line associated with it, right-clicking, and selecting delete from the menu.  You can leave the swap partition alone...it will be automatically used by the installer.

Once that is done and the partitioner re-scans and shows free space, select the line associated with the free space, right-click, and select "New" (I think there is also icons that you can use...I can't remember exactly).  You will be presented with a dialog box with various selections.

The first selection will be the partition size.  If you don't intend to use separate "/home" or other partitions, it's OK to use the entire free space, but if you intend to install other partitions and want to leave room for them, then you can decrease the size of the new partition to whatever size you desire (as long as you have at least 8 GB or so for a minimal installation).

The next selection will be grayed out if you use the whole free space, but if it's less then you will be presented with two radio buttons with which you can select to make the partition at the beginning or end of free space.  If you intend to install a separate /home partition, make your root ("/") partition at the beginning (which is default) of free space (around 8-10 GB if you have room...if not, I suggest at least 5GB), then create the "/home" partition behind that.

Next selection will be the file system type.  Click on the little box and you will be presented with a list of file systems that you can format the partition to.  Among them will be ext4, which you need to select (default is ext3, which is why Guided used ext3 for your installation).

After that is the Mount Point selection drop-down.  click on the little box and you will be presented with a list of mount points; among them "/" (root, which you should select if you're doing a single partition install), "/home" (which you would select for the second partition if you're installing a separate home partition), and several others.  This is where you select the mount point for the partition you're creating under the Manual partitioner.

You can find a lot of good information on basic partitioning operations and concepts at this page:

[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

I haven't had a chance to update it for Jaunty and the ext4 file system, but the basic operations and concepts are largely the same.  Any other questions; just ask.  I, or someone, will guide you further.
):P

---

### Post by -kg- on 2009-04-29
> **rreyes3000 said:**
> That is where I got confused. I was confused with the set partition step and the mount points. There was a drop down menu that gave me all sorts of file system options. I selected ext4 then went to the next step. This when I got a window that stated I needed to set a swap partition.  Actually, I have been working with ubuntu for about two weeks and my exact memory of what I encountered is hazed. I have so much new info floating around my membrane and going insane:P  So . . . is the window that pops up used to setup my swap partition? Do I use 1.5 times the amount of ram I have? By doing so, is the rest of the drive I formated to ext4 left as is and then the OS installed on it?

Told you I was confussed?!

It takes me sooo looong to compose my posts! :lolflag:

Yep, you needed to set a swap partition.  You likely made the whole disk a big ext4 partition.  The very best thing is to make the swap partition first, at the very end of the disk. When you make the swap partition, you format it as Swap from the list.  You don't need to mark it as swap...it becomes that due to the formatting.

And yes, 1.5 X the amount of RAM is a good size, though you might need more or less depending on how much RAM you have and whether you're going to hibernate the computer or not.  I have 2 Gigs of RAM and don't hibernate.  I've never once used the swap partition for anything.

The you create the / (root) partition in the remaining space, as big as you want to make it, and selecting ext4 as the format.  Once you have both those partitions made (and of course, marked the ext4 partition as root), you're good to go.

---

### Post by theozzlives on 2009-04-29
> **-kg- said:**
> It takes me sooo looong to compose my posts! :lolflag:

Yep, you needed to set a swap partition.  You likely made the whole disk a big ext4 partition.  The very best thing is to make the swap partition first, at the very end of the disk. When you make the swap partition, you format it as Swap from the list.  You don't need to mark it as swap...it becomes that due to the formatting.

And yes, 1.5 X the amount of RAM is a good size, though you might need more or less depending on how much RAM you have and whether you're going to hibernate the computer or not.  I have 2 Gigs of RAM and don't hibernate.  I've never once used the swap partition for anything.

The you create the / (root) partition in the remaining space, as big as you want to make it, and selecting ext4 as the format.  Once you have both those partitions made (and of course, marked the ext4 partition as root), you're good to go.

You create the swap, / (root) should be 10-20 GB, the rest is /home.

---

### Post by -kg- on 2009-04-29
> **theozzlives said:**
> You create the swap, / (root) should be 10-20 GB, the rest is /home.

Yes, if you want a separate /home partition, as I said in the first post.  And I think 10 GB is plenty for root.  My Hardy installation had *_gads_* of software installed, along with all three desktop managers and their associated default software, and I never used over 5GB in my root partition.

Of course, it all depends on what you want to do.

Oops...just noticed.  Guess I'm going to have to go into my profile and change from Hardy to Jaunty.

---

### Post by rreyes1316 on 2009-04-30
WUTTA WUT HUH!!!?

Should I create the swap first?

I thought the / mount is where ubuntu is installed. On my 200GB extra drive I allocated 10 GB. That should be enough for ubuntu to breathe with update and other programs, right?

The swap I made 4GB, twice the amount my RAM.

The remainder has been alloted to the /home mount.

In fact, not even sure I need that much since i will have a TB drive that has all my audio, video, docs, etc, stored on it.

The 200GB drive is the one I am playing with. My original OS, which will only house ubuntu and not dual boot is a WD Raptor 150.  

Hope I am not confusing you.

---

### Post by rreyes1316 on 2009-04-30
Also, if the swap is a primary, when givven the choice, what should the / and /home be? When I created each partition it defaulted to logical except for the swap partition.

---

### Post by rreyes1316 on 2009-04-30
OK From what I have read and contemplated:

10GB / ext4  primary
85GB /home ext4 logical
5GB swap primary (at the end)

The above is a sample based on a 100GB hard drive.

Is this how it would be set up? Primaries are for os's and logical is for storing data, roughly.

---

### Post by rreyes1316 on 2009-04-30
Perhaps the last question--SDA's. Does it matter if each of the mentiones partitions are not in chronological order(i.e. sda1, sda2, sda3, etc)?

---

### Post by Sef on 2009-04-30
> 10GB / ext4  primary
85GB /home ext4 logical
5GB swap primary (at the end)That would be fine except for swap.   Swap should not be more than 1 gb.  If you are doing something extremely graphics intensive then with 2 gb or more with 2 gb ram.   If you need more swap than that, then you need more ram.  The old rule about 2 times the amount of ram does not apply to 1 gb and above.

> Does it matter if each of the mentiones partitions are not in chronological order(i.e. sda1, sda2, sda3, etc)?

No.

---

### Post by rreyes1316 on 2009-04-30
> **Sef said:**
> That would be fine except . . .

Wonderful! Then I am ready to put everything on my maid drive. But with the above mentioned, what would be an ideal setup? Is there another configuration you suggest? I am sure there are many. I just dont want to look bac six months from now and wish i had done it differently--but I cant see the future.

Thank for all you help folks. I feel like a Newbie level III:lolflag:

---

### Post by -kg- on 2009-04-30
Good Morning!  (Nearly afternoon!)

Yeah, that configuration sounds fine.  Like Sef said, the swap size is a little excessive; like I said, I have a swap partition that I have never used.  It all depends on what you plan on doing (or what you happen to fall into in the future) that will determine if you are using software RAM-intensive enough to even justify a swap file at all.  Like I said, if you hibernate you'll need a swap file roughly the size of your RAM or just a bit bigger (1 1/2 times is *very* safe) in which to store the RAM for hibernation.

Now I just noticed; you plan to make the swap primary?  If you're going with root as a Primary partition, then that's OK, though not necessary.  Make your root partition, then surround the entire remaining free space by an Extended partition and create the /home and swap inside it.  Of course, I personally would make the swap partition first, right at the end, then use the remaining free space for /home.  It's easier than trying to create the /home partition and leave just enough space for the small swap file.

Linux will run totally from within an Extended partition, and you save yourself running up against the 4 Primary partition rule in the future.  Of course in your setup you're not likely going to run up against that problem, but it can create confusion if you're not really aware of the function and manipulation of an Extended partition (boy have I run into *that* in these help forums! :P ) and the Logical partitions therein.  If you enclose the entire drive in an Extended partition (Linux will run totally from within an Extended partition, unlike most Windows installations), that basically eliminates the problems, but it's alright to have a partition or two as Primary.  Depends totally on you and what you think.  Just remember the 4 Primary partition limit.

If you've already done the partitioning and install, and you really want to (say for experimentation :) ), the swap can easily be moved inside the Extended partition later, using either the partitioner on the Live CD or, alternatively, you can download the GPartEd Live CD that I linked to above.  It's really a good tool made specifically for partitioning operations.

As far as alternative (future) partitioning schemes, Linux partitions are easily re-configurable.  You can resize partitions and add new ones, move them within free space, re-format and re-use them, and easily back them up to CD/DVD or another hard drive or partition, using a number of backup tools available.  See the Community Wiki page I linked to above; it's a real good resource for basic partitioning operations.

Can you tell by now that I've partitioned many hard drives over the last 10-15 years? :lolflag:

Years back, before LBA and such, it was almost necessary for the larger hard drives because of the minimum sector size limitations in FAT.  Nowadays it's not, but it comes in handy for multiple OSes.

Something I would suggest to you (which I have) is an external hard drive to do your backups to and storage for your important files (like pictures, music, videos, and even email files).  You can share it between computers (which I do); even those with Windows, if you make one or more of the partitions a Windows partition.

I'm kind of a nut-case. :lolflag: I have around 220 GB of internal hard drives in my laptop, then I have a 1 TB external drive which I largely use with it.  I store my music, video, and backup files on it, and I store and access my email files (through the Thunderbird email client) on it.  I can, at will, switch it to my desktop for access.

My desktop has 2 IDE hard drives...1 400 GB Primary and a 120 GB slave (which lately I've been using for partitioning experimentation and demonstration for the page I linked to above), and a 1 TB internal SATA drive.  Between the external TB and the internal TB drives, I have multiple backup redundancy, and I have my music files backed up to 6 DVDs, to boot.

I don't like to lose data, and I've done some video editing in the past, with large video files, so I needed the room for work and storage anyway.  Good luck, and have fun!

---

### Post by ezsit on 2009-04-30
Yet one more opinion about partitioning...

I have three computers all running Linux as their sole OS. I partitioned the space as follows:

sda1  --  swap, 2GB, primary
sda2  --  / (root), 30GB, primary
sda3  --  data, 200GB, primary
Remainder of the drive left unallocated

I leave /home within the / (root) partition and keep all my data on the /data partition with symlinks back to /home. In case I need to reinstall, all my data is safe and free from the rest of the system and I am free to cleanly overwrite the / (root) partition. Since I know that I never want to run more than one OS on the computer at a time, I use primary partitions and only use three, just in case I may need an extended, logical at some future time.

That's just me. I don't use Windows at home (just at work, like now, sshh! don't tell anyone!).

---

### Post by rreyes1316 on 2009-04-30
Using swap as primary was what the settings defaulted to. Told you I did not know what i was doing :)  It just happened that I created swap first as suggested and moved to the end. Correct me if I am wrong but I should create swap an place at the end (extended?), then / as primary (?), then the remainder as /home extended. Actually, it is hard trying to reply on the post usug my phone. I will try tomake self more sense when I get home on pc. 

BTW, I have a terabyte that has everything and being used as you mentioned. Also have 4 200gb drives to play with as you mentined for partionining testing and OS's. My sytem os is on the Raptor 150. So actally, I am not even sure I should fret too much over how I partition--but it's fun!

---

### Post by -kg- on 2009-05-01
> Using swap as primary was what the settings defaulted to. Told you I did not know what i was doing It just happened that I created swap first as suggested and moved to the end. Correct me if I am wrong but I should create swap an place at the end (extended?), then / as primary (?), then the remainder as /home extended.

It seriously matters not at all.  It doesn't matter what order the partitions are on the hard drive, nor whether or which partitions you make Primary or Logical, at least as far as Linux goes.

The only reason I suggested you put everything in an Extended partition is the "4 Primary Partition rule."  Linux will run from an Extended partition.  If at some point you decide to create different partitions (like ezsit's "/data" partition), or experiment with different Linux distributions or other OSes, then you are not limited by the primary partition rule.  You can create up to 63 Logical partitions (which you not likely to need) in the Extended partitions on each drive you have.

Experiment away!  Learn and try different things.  Just back up information that you absolutely don't want to lose.  If you screw up, no big loss...just try to correct it, and if you can't, reinstall.  After all, Linux is free and won't require you to pay a price for any number of reinstalls that you are forced to do.

I can't tell you how many times I was forced to reinstall Windows due to my messing around with it, and though I was never called to task, I paid the price in the beginning (something near $200 for Vista Home Premium, which I have never used yet), and it is in the EULA that I might have to ask permission.  All I did was download Ubuntu and install it, and will be able to reinstall it at will, any number of times and for any reason without asking a major corporation's permission.

Personally, I like that!:grin:

---

