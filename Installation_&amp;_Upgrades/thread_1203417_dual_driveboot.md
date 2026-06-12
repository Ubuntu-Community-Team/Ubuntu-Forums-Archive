---
title: "dual drive/boot"
date: 2009-07-03
forum: Installation &amp; Upgrades
---

### Post by foxyid on 2009-07-03
I am totally new to linux/ubuntu. 

I have read through the basics of installation and dual-booting and everything seemed straightforward.
But since I had some unanswered questions, I ventured into the forums for more informaion, and what seemed to be "simple" when i started off, has become more and more complicated.  Maybe someone can bring me back to that simple state.

I already have WindowsXP installed and want to install Ubuntu on my second hard drive (300gb); I use this second HD for Windows' paging file and for backup/storage (an extended partion of 200gb), so I have about 100gb for Ubuntu, which should be more than enough.

Is this setup acceptable? Is there a preferable position for Ubuntu's disk partition or can Ubuntu reside anywhere on the HD?

I want Ubuntu to access the Data/Media I have on my first HD, in an extended NTFS partition.  I am assuming this should not be a problem.  Are there any issues that I should be aware of?

How should I partion Ubuntu?  When do I do this, during installation or after?  

Thanks for all of the help.

---

### Post by Idefix82 on 2009-07-03
Hello and welcome!

Your plan is completely reasonable and you should have no problems along the way. Ubuntu should automatically recognise the ntfs partitions after you install it.

You should have at least two partitions for Ubuntu, one for the main system (mount point /) and one so called SWAP partition. The latter will be used for example for hibernate when Ubuntu will write the entire memory into the SWAP. As such, it should have about the size of your RAM. It will also be used if your RAM doesn't suffice, but personally I never had that happen.

You can also have a separate /home partition, where your personal settings and data will sit. That will make upgrading easier, since you will be able to install a completely new version of Ubuntu while keeping your settings and data untouched. If you decide to have a /home partition then give it by far the most space. I'd say 10GB for the main partition, amount of RAM for SWAP and the rest for /home.

As for the position of the partitions of the hd, I would recommend the / partition at the front, then the /home partition, the SWAP partition at the very back. That's because the SWAP will be mainly used to write large chuncks of data in one go and the longer outer circles on the hd are perfect for that in terms of speed.

To do this whole thing, defragment the hd several times from Windows, then resize the partition, move it to the desired position, then boot from the live cd and set up the Ubuntu partitions during the install. Ask away if you run into problems.

Backup the data if you can, since resizing and moving partitions is always a risk.

---

### Post by foxyid on 2009-07-05
Thanks for the quick response

I did some rethinking and, since the second HD is a new purchase and I have not yet dumped any data on it, I decided to remove the NTFS storage partiton and install Ubuntu first. No reason to resize and move partions if this is unnessary.   I am assuming that it is better that Ubuntu should be positioned closer to the front of the disk rather that the back (like Windows which sets up C: first at the front of the disk).

This is what I am looking at on my second HD:
I already partitioned a Fat32 partition at 6gb for the Windows paging file and I will leave that in place.
Next will be Ubuntu, for which I have set aside 100gb.
After Ubuntu is installed I will create, from Windows, a new NTFS partition, about 200gb, for backup/storage dump.

So my only questions are about specific Ubuntu patitioning.

You said that the / (root) partion should go first, in the front. 
Should I choose the location for this partion as: Beginning?   Will there be a conflict with the Windows Fat32 partition that I created before Ubuntu for the paging file?  (What does Beginning really mean?)  
I am assuming this has to be a primary partition (not a logical partition).  
10 gb is enough?  
Is it possible to seperate programs (non-default Ubuntu apps) from the / (root) partition?  If so, which partition should they be placed in?

How big should the /home position be?  If I am  accessing the bulk of my data (pictures/audio) from Windows NTFS partitions, does the /home partition need to be so big?  
Should this partion be primary or logical?  
Should I set the location as Beginning or End?

How big should the Swap partion be?  I read somewhere max. 2gb and in other places read 2*RAM. I have 4gb RAM so should I go with 2 or 8?  
Should this partition be primary or logical?  
You said that the Swap partition should be position should be at the very back.  Should I set the location as End?  Will there be a conflict with the Windows NTFS partition that I wanted to create after Ubuntu for backup/storage dump?  (What does End really mean?)

Should I concern myself with all of the other partitions that I saw listed in Ubuntu documentation?
Like /boot or /tmp or /usr?
100gb seems like alot considering that I will be utilizing/sharing my data from Windows partitions.
How should a beginner maximize everything Ubuntu has to offer?

Thanks for all the help.

---

### Post by Idefix82 on 2009-07-06
Ok, I hope I don't leave out any of your questions.

If you tell the installer to create a partition, it will automatically use unallocated space, so it won't delete any existing partitions. With "Beginning" and "End" you choose where in the unallocated space the new partition should begin.

Now for the exact partitioning. A minimum setup would just have a / and a SWAP partition. However, there are reasons why you might want to create more partitions. I wasn't going to bore you with that, but since you asked, here are the separate partitions, that I have, together with reasons for having them and corresponding sizes:
[LIST]
[*]A separate /boot partition (about 80-100 MB to allow for several kernels at the same time, you will need space for at least 2 kernels, whenever a kernel upgrade comes out) for slightly increased failure-proofness. Even if you screw up your / partition you will still be able to boot. This is the only partition that needs to be primary (you have to make / primary if you don't make a separate /boot partition) and it should be as close to the beginning of the disk as possible.
[*]A separate /var partition. This folder is used, among other things, for storing log files. Under certain (rare) circumstances those can start piling up too quickly and by having them in a separate partition you prevent the hard drive from filling up. This is definitely recommended, if your computer will function as a server for anything (like ssh). This folder is also used for temporarily storing packages that the package manager downloads. For that reason, I would give this partition at least 2GB, because sometimes it's handy to keep some installation files on the computer, e.g. if you want to re-install something without having to run a large download again.
There is also an other reason for having this as a separate partition. Files in /var have a fairly low life span. By keeping them in a separate partition, you will keep fragmentation of the remaining drive to a minimum (note that ext3 doesn't really get fragmented, but that's because it constantly defragments itself).
[*]A separate /tmp partition, mainly for the last reason listed in the previous bullet point. Around 300MB should suffice for this, unless you are planning to run computationally intensive software of which you know that it uses /tmp for temporary data. Then, you might want to play safe and give it 1GB, but note that this is likely to stay empty most of the time. So this is very optional, I'd say.
[*] A separate /home partition for two reasons. Firstly, the life span of these items is somewhere between that of /boot and /var. So if you decided to give /var and /tmp separate partitions to minimise fragmentation then the same reason applies to /home. Secondly and much more importantly, this is where you would normally store personal documents, other data and also personal settings. All those are things that you want to keep between installs of different versions of the OS, and having them in a separate partition makes upgrading dead easy. The size of this depends a lot on your circumstances. For example, in your case, you will probably not store lots of films or music on this partition, so it needn't be that big. It depends on the number of users, etc. but just for settings and text documents, even 5GB will be total overkill. (Some programs use more space on /home if they have it, e.g. the screensaver [electric sheep]("http://community.sheepserver.net/") and if you don't want to ever even think about space restrictions on /home then give it 10GB.)
[*]Finally, the / partition. Most of it will be occupied by the content of /usr, where all the program binaries will sit. For that reason, some people give /usr a separate partition, but I think that's unnecessary. 10GB for / will never see you worry about space for software unless you install everything available in the repositories(and much much less might in fact suffice). If you have created a separate /boot partition, then no other options matter for /. Otherwise, / needs to be primary and should sit as far on the front of the disk as possible.
[*]The size of SWAP is a subjective matter. On the one hand, with 4GB of RAM, your SWAP will never be used, unless something is badly wrong with the computer. On the other hand, if you hibernate, what happens is that the content of the RAM is written into SWAP. So if you want to use hibernation, you want SWAP to be large enough. 3GB should almost surely suffice. The thing about "twice as much as RAM" is, in my opinion, only applicable to computers with very little RAM where SWAP will be used a lot.
[/LIST]

I hope your head is not spinning after so much input. If it is and you don't wan't to think about these things, then just make a primary / with 10GB of space, a /home with about as much and 3-4GB SWAP. The setup I described aims at maximising speed of hd access and security but it is more wasteful on the hd than it could be.

---

### Post by foxyid on 2009-07-08
Thanks for the instruction/education.

So there will not be a conflict with the small Windows partition I already created at the beginning of the disk.
Choosing "Beginning" only sets the specific partition closest to the beginning of the disk as is possible.  This is relative to what has already been created, a preexisting partition, or within the unallocated space of the disk itself.  

If I choose "Beginning" for each Ubuntu partition, I would be telling the installer to choose the first unallocated space after the previously created partition. The Installer would set the partitions in the order that I choose. The first would be at the relative beginning, followed by each successive partition.

But what about choosing "End"? This should set the specific partition to the farthest section from the beginning of the disk, within the unallocated space.  What is the point of choosing End? Just let the last (in order of setup) be created last.

Does the Installer set up Ubuntu as one continuous section on the disk?  
The setup size that you recommended comes out to about 26gb.
After my 6gb Windows partition, Ubuntu's /boot partition will be at the "beginning" as you instructed (followed by the rest of the partitions). 
If I choose End for the Swap partition, where will it be created?

Sorry for the tedious questions, but i want to know if there will be a conflict when I create a Windows NTFS partition after installing Ubuntu.

Another question:  Why do you think that it is unnecessary to separate programs from the / partition and place them in a separate /user partition ?  I understood that when installing a new Ubuntu version, the / partition is the one that gets reformatted. I always hate having to reinstall all of my programs whenever I have to reinstall Windows (programs default to C:\ and it is practically impossible to separate them by creating a specific program partition).  So if it easy to do it in Ubuntu, why not set it up that way?

Following your recommended setup I will install as the following:
1. /boot - 100mb - primary - beginning
2. /var  - 2gb   - logical - beginning
3. /tmp  - 1gb   - logical - beginning
4. /home - 10gb  - logical - beginning
5. /     - 10gb  - logical - beginning
6. /swap - 3gb  - logical - end

Is this the correct order and choices?

One last question:  If /boot partition is sitting after a 6gb partition on the disk (after 2% of the disk), is this acceptable?

Thanks again for all the information and help.
Have a great day.

---

