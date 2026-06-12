---
title: "Missing swap partition"
date: 2005-06-03
forum: Hardware &amp; Laptops
---

### Post by macquigg on 2005-06-03
When I run the automatic install, it uses the entire free space on my disk.  When I try to set up the partitions manually, it doesn't give me an option to add a swap partition.  The help screen says "some users feel that a swap partition is needed".  What kind of language is that for a new user.  How do the developers feel?  They are the ones that know for example, what will be the impact on performance.

Note: I am using a 4.10 install disk, then upgrading from the Internet.  I assume that gets me to 5.04, but I can't see that confirmed anywhere.

Help will be appreciated.

-- Dave

---

### Post by az on 2005-06-03
If you let ubutu do the patitoining, it will give you a swap.  If you do it yourself, you have to do it yourself.  What else can I say?

[http://test.wiki.ubuntu.com/forum/installation/Partitioning](http://test.wiki.ubuntu.com/forum/installation/Partitioning)

---

### Post by defkewl on 2005-06-03
But did your ubuntu worked without the swap partition? This is rather  strange  :roll:

---

### Post by macquigg on 2005-06-04
It seems to be working without any swap partition.  My worry is that this will hurt performance when I get the system fully loaded.  Maybe it is doing like Windows, and putting the swap file in the main partition.  Nautilus doesn't show me any strange files under / however, even if I set the "show hidden files" option.

I still can't figure out how to manually add a swap partition.  Has anyone else had this problem?  Is it because I did the initial install from a 4.10 CD?

---

### Post by az on 2005-06-04
A swap will not improve your performance.  It will keep application running when you run out of memory for them.  It will slow your system to a crawl.  

No, the reason you do not have a swap is not because you installed with Warty.  It is as you yourself have said, you did it manually and you did not create one.

Read the link on partitionning.  You need to partition to create a swap.  After you partition, you need to add an entry in your fstab.
/dev/hda5     none     swap     sw     0     0

---

### Post by macquigg on 2005-06-05
The procedure with fstab looks a bit hairy.  The note on partitioning is good.  Looks like there is a better chance of getting it right with Hoary.  The note says  the Warty installer did not have partitioning functionality, but the Hoary installer does.  I'm downloading Hoary now.  I'll let you know theresults later.  P.S.  I did the original partitioning with Partition Magic.

---

### Post by macquigg on 2005-06-05
I installed from the 5.04 CD, and got the same problem.  The Guided Setup uses the entire free space, and there does not appear to be an option to limit the size of the new partition without getting into the complexities of manual setup with fstab.

What I did to get the setup I want is partition the disk with Partition Magic, leaving just the amount of free space I wanted for the Ubuntu partitions.  Then running the automatic Ubuntu install creates the needed partitions out of the free space.  They are set up as logical partitions.  I assume that is OK.

The documentation on the installer should be clarified.  This really isn't a full-featured partitioning program.  If you want Ubuntu to occupy just a small piece of your disk, use a real partitioning program first.

Other than that, the install went smoothly on my HP Pavilion laptop.  I'm delighted with  the Synaptic package installer.  I always knew package installation could be easier, but Synaptic is even better than my expectations.  

Thanks to azz for pointing me in the right direction.

---

### Post by az on 2005-06-05
Warty can partition hard drives, just not ntfs filesystems.

Guided partitioning creates a root and a swap automatically with all the free space it finds.  If you want to resize what it offers you, you just have to go back to the partition table before you accept what the guided partitioning offers you.  You can change the values to your liking.  Any partition and filesystem you create that way gets an fstab entry.  You just have to give it a name and filesystem type and so forth.

It does it all.

---

### Post by macquigg on 2005-06-06
That works!  I just didn't spend enough time poking around to realize I could resize partitions *after* doing the automatic setup.  Cool.  Thanks again, azz.

---

### Post by JohnEo on 2005-06-09
I'm also swapless under Hoary.   I also reduced the zone free on my disc with Partition Commander. Installed Ubuntu 5.04 from a DVD that came in Linux mag and it works fine except there is no SWAP.  I already had Mandrake (with its own Swap in a Logical Part) and Windows plus two FATs for data.  Apparently the Ubuntu installer could not make its SWAP because of the limit of 4 principals parts  on one disc.
Since then, but now with GParted under Ubuntu, I unallocated one of the FATs, sliced off 510mb and formatted it as Linux-Swap.   

Now ubuntu [/dev/hda4] and linux-swap [/dev/hda3] are just sitting there
(the linux-swap is flagged "lba").

To access the FAT partition, i used the suggested plan so it comes in as MEDIA under Ubuntu.  Is there something equivalent for the SWAP file?

---

### Post by macquigg on 2005-06-09
Hi John.   Now that I have a little more confidence in Ubuntu's partitioner, I would recommend doing the minimum with some other partitioning program, and letting Ubuntu do as much as possible of the setup, hopefully avoiding edge cases, like maybe you have too many primary partitions to start.

What worked for me is starting with only two primary partitions and 28GB of free space.  The max is 4 primary partitions, so that seems to allow room for a fresh install.  I used the Ubuntu installer to set off the last 16GB of the free space as an ext3 partition, which I will use for future expansion or temporary data.  I like to keep my active partitions small, so they can be easily backed up.

Then with the remaining 12GB of free space, I ran the automatic partition install.  This gave me an ext3 root partition and a swap partition, both set up as logical partions within the 12GB.  I assume there is no problem with using logical partions instead of primary.

Hope this helps.

-- Dave

---

