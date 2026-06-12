---
title: "What partitions do I have to have?"
date: 2009-08-08
forum: Installation &amp; Upgrades
---

### Post by Cavsfan on 2009-08-08
Hi! I am trying to install Ubuntu 9.04 on my PC. I have created the installation CD and almost installed it last night, but got confused about what format to use to partition.
I have Vista 64 bit and Windows 7 64 bit RC in a dual boot system and they have their own partitions. I created a 44GB partion that I want to install Ubuntu on. I will probably eventually delete one of them and enlarge the partition Ubuntu uses.
When installing, the top option was to boot this along side Vista. I choose the Custom installation (I believe at the bottom) and became confused at that point.
I got more confused when I read through the documentation about partitions in Ubuntu.
I believe I need an Ext3 partition and a SWAP partition, but then I seen something about /usr, /var, /tmp and /home partitions.
I would like to create a system for possibly 3 users if I can.
 
I am really looking forward to this as I have read a lot of very good things about it. :D
I also used to work with Unix based servers at work and so I am at least a little familiar with the commands.
Should I take the "boot along with Vista option" or the option that I took and what do I choose from there?
Thanks in advance! :)

---

### Post by stlsaint on 2009-08-08
well you didnt give quite enough information for us to help you with all your issues but i will do what i can..well yes you can have all three running together(i used to) but you dont want to choose the install side by side option for what you are trying to do! choose the manual option so it will take you to the partition page, from there you want to make sure that your ubuntu partition is deleted so it says free space! than you want to select that free space and select to create a partition, this will be your SWAP area...i make mines about 1GB or 1024 is the number your gonna type in for size! its up to you how big you want it!! now in the mount point drop down box select swap area then ok, now your back to the partition page, there select the rest of the free space and choose create partition, (now here is where it becomes your decision again) if you want the rest of the 42GB for your boot which will hold boot files, data flies ,etc than select the default size as the size of the partition and for the mount point choose (/) then ok and make sure you choose either ext3 or ext4. 3 is more stable but 4 is newer! if you want more partitions out of the free space ie( /home, /boot/etc) just do the same thing you did for the swap are but instead of selecting swap choose whatever you want the mount point to be!! hope this was what you were looking for(YOU ONLY NEED THE SWAP AND / POINTS TO INSTALL UBUNTU, EVERYTHING ELSE IS A CUSTOM INSTALL!!)

---

### Post by ratcheer on 2009-08-08
Here is some advice that I followed and it is working very well, for me.

1) Create a swap partition equal to the size or your machine's RAM. If you are not comfortable with that, make it double the RAM.

2) Create / as a logical partition of 10 to 20 GB.

3) Split the remainder of your available storage in half, one half for /home and the other half for /usr.

YMMV, but this is a fairly simple, usable arrangement.

Tim

---

### Post by raymondh on 2009-08-08
I have used [Bodhi's]("http://ubuntuforums.org/showthread.php?t=282018") guide to understand partitioning.

Good luck and back-up.

---

### Post by Cavsfan on 2009-08-08
Thanks to all of you for your generous help getting me started. :D
I am ignorant now about all of this, but in a short while I will be a novice! :guitar:
I was almost there with the installation and backed out with this question:
Where it was going to partition the SWAP file it had a check box for
Create a New Partition [ ] Primary or [ ] Logical.
I figured I should put Primary, but thought I had better ask.
And would I select Primary on each partition created?
(also I freed up another 5GB for the installation and I would like to know where that would best be fitted below? In the SWAP partition maybe?)
I now have 49.15 GB available.
 
I have 4MG of RAM
So I have this scenario in mind:
SWAP: 8MB (8192)
/ext4: 20MB (20480)
/boot 1.5MB (1536)
/usr 1.5MB (1536)
/var 1.5MB (1536)
/tmp 1.5MB (1536)
/home 1.5MB (1536)
Does this sound good?
I think this is some fantatic stuff and I am anxious!
Thanks a lot for all of your help!!!

---

### Post by raymondh on 2009-08-08
> **Cavsfan said:**
> Thanks to all of you for your generous help getting me started. :D
I am ignorant now about all of this, but in a short while I will be a novice! :guitar:
I was almost there with the installation and backed out with this question:
Where it was going to partition the SWAP file it had a check box for
Create a New Partition [ ] Primary or [ ] Logical.
I figured I should put Primary, but thought I had better ask.
And would I select Primary on each partition created?
(also I freed up another 5GB for the installation and I would like to know where that would best be fitted below? In the SWAP partition maybe?)
I now have 49.15 GB available.
 
I have 4MG of RAM
So I have this scenario in mind:
SWAP: 8MB (8192)
/ext4: 20MB (20480)
/boot 1.5MB (1536)
/usr 1.5MB (1536)
/var 1.5MB (1536)
/tmp 1.5MB (1536)
/home 1.5MB (1536)
Does this sound good?
I think this is some fantatic stuff and I am anxious!
Thanks a lot for all of your help!!!

Chances are, you already have 3 primary partitions in your HD.  I say 3 because of Vista, Win 7, and (probably) a OEM recovery partition.

We all have a 4 partition limit per HD ... whether it be 4 primary or... 3 primary + 1 extended.  That being the case, that 49 GB ought to be an EXTENDED partition and, all your preferences (i.e. swap, root, boot, var, etc.) be logical partitions inside the Extended.

---

### Post by Cavsfan on 2009-08-08
> **raymondhenson said:**
> Chances are, you already have 3 primary partitions in your HD.  I say 3 because of Vista, Win 7, and (probably) a OEM recovery partition.

We all have a 4 partition limit per HD ... whether it be 4 primary or... 3 primary + 1 extended.  That being the case, that 49 GB ought to be an EXTENDED partition and, all your preferences (i.e. swap, root, boot, var, etc.) be logical partitions inside the Extended.

Thanks a lot! I will try that.
I appreciate the help!


:popcorn:

---

### Post by Cavsfan on 2009-08-08
I am using Ubuntu!
Thanks for your help.
I have one question though:
It wants to update a bunch of stuff (226MB) on /usr
and I made it 2048MB but it says there is not enough room.
Any ideas on what I should do?

Sorry if I am being a pain, but I am a newbie on Ubuntu.
Thanks!

---

### Post by ratcheer on 2009-08-08
> **Cavsfan said:**
> 
I have one question though:
It wants to update a bunch of stuff (226MB) on /usr
and I made it 2048MB but it says there is not enough room.
Any ideas on what I should do?



How much space (total) do you have for Linux? 2048 MB for /usr is not nearly enough - that is where most software gets installed, kind of like the Programs folder in Windows. My /usr is 28GB, but I am using all of an 80GB drive for Linux.

Tim

---

### Post by dE_logics on 2009-08-08
Make all the system partitions reserfs and your personal partitions JFS (if you're using mixed files in it).

But JFS has a major problem...if you every do an improper shutdown, it becomes corrupt...so you gotta recheck it after that.

The process can be made automated by modifying fstab.

---

### Post by Cavsfan on 2009-08-09
Thanks for the help!
I think I figured out where I went wrong last night about 10 PM.
I created logical partitions for everything as I mentioned above.
I have about 50GB to use for the install, so I will reinstall with the SWAP
as a logical partition - 8MB (double my RAM) 8192 and I will give the rest to / ext4 as a
primary partition and just leave the OS to determine the rest.
I see no option for Extended partition, so I will try this.
I think I shouldn't have created all the 2048MB logical partitions for all of the other stuff.
I'll try this and see what happens.
Thanks again!

---

### Post by Cavsfan on 2009-08-09
Well, I am in!
It installed great this time and got all of the updates.
I think it took about 5 seconds to load!
I set the desktop graphics to the best and it downloaded the drivers and now everything
is cool beans!
Thanks for all of your help.
I will do some "poking around a bit" now to learn some more about this great operating
system. I definitely have a lot of learning to do!
:)
I choose ext3 instead of ext4. Can that be changed at some later point if desired?
Thanks again!

---

### Post by Narada on 2009-08-09
> **Cavsfan said:**
> I choose ext3 instead of ext4. Can that be changed at some later point if desired?
Thanks again!

Yup. ext4 is also backwards compatible with ext3 and ext2.

---

### Post by raymondh on 2009-08-10
> **Cavsfan said:**
> Well, I am in!
It installed great this time and got all of the updates.
I think it took about 5 seconds to load!
I set the desktop graphics to the best and it downloaded the drivers and now everything
is cool beans!
Thanks for all of your help.
I will do some "poking around a bit" now to learn some more about this great operating
system. I definitely have a lot of learning to do!
:)
I choose ext3 instead of ext4. Can that be changed at some later point if desired?
Thanks again!

Congratulations and Happy Ubuntu-ing :)

---

