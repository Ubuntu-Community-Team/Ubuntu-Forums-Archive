---
title: "Not enough memory..."
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by velopimp on 2009-07-02
hey all,

i am new to this place and new to ubuntu.  i know that i can probably find everything i need here, and there is no need to ask questions that have been asked 1000 times, but i still feel like opening a dialogue would benefit me, so here it goes.....

i installed ubuntu on my 2.5 year old dell, and it was like hitting it with a defib.  i thought my computer was a total pos, but with ubuntu it performs very well.

unfortunately, my ubuntu installation has no memory.  i thought that it would partition itself an appropriate chunk of memory, but it did not.  and now i have a ubuntu installation and i dont even know exactly where it is (its own partition or not??).

i realized this when i booted up and ubuntu wanted its updates.....  there was not even enough memory to download updates.

now that i have seen ubuntu operate on my machine, and i like it a lot, i am ready to devote as much of my system to it as possible, leaving vista only for games and a few engineering apps that i have......  but i dont know how to fix what i have done already.

i have noticed that i have access to the windowns file system while inside ubuntu, but not the other way around as well.  is this correct?

also, what is a swap?

id like to add that i'm not very dumb, i'm just very new :) ...........

thanks

---

### Post by merlinus on 2009-07-02
You are talking about hard disk space, not memory (RAM).

Open a terminal and post results of these commands:

```
df -h
sudo fdisk -l
```l is a lowercase L

Your swap partition gets used when the computer is using all of its RAM.

---

### Post by velopimp on 2009-07-02
correct, and thank you for your reply.  i did mean hard disk space and not RAM.  

here is the output from the command window:

t@t-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             2.3G  2.2G   60M  98% /
tmpfs                 501M     0  501M   0% /lib/init/rw
varrun                501M   92K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M  164K  501M   1% /dev
tmpfs                 501M  476K  501M   1% /dev/shm
lrm                   501M  2.4M  499M   1% /lib/modules/2.6.28-11-generic/volatile
t@t-laptop:~$ sudo fdisk -l
[sudo] password for t: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7       13367   107322232+   7  HPFS/NTFS
/dev/sda3           13368       13954     4715077+   f  W95 Ext'd (LBA)
/dev/sda4           13955       14593     5132767+  db  CP/M / CTOS / ...
/dev/sda5           13694       13954     2096451   dd  Unknown
/dev/sda6           13368       13671     2441817   83  Linux
/dev/sda7           13672       13693      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order
t@t-laptop:~$ 
t@t-laptop:~$ 


i'm not gonna lie.... most of that doesn't mean anything to me.....  except that it appears i only have enough room for the os itself(?)

---

### Post by merlinus on 2009-07-02
/dev/sda6             2.3G  2.2G   60M  98% /

You only gave ubuntu 2.3G of space, and 98% is already used up.  It needs at least 5-7G. And nothing else in the extended partition has much room either.

Your best choice at this time is to try and shrink your windows partition more, and then reinstall ubuntu.

You might try using gparted to add this partition's space to linux:

/dev/sda5           13694       13954     2096451   dd  Unknown

but it still will fill up very fast.

---

### Post by velopimp on 2009-07-02
i guess i figured ubuntu would help itself to a decent partition automatically (i chose the automatic install).....

not the case....

so if i have this correct, what i should do is resize the windows partition and reinstall ubuntu?  

can that be done without reformatting?

also, if i were to simply try to reinstall ubuntu, could i just resize there?

thank you so much for taking time to help

---

### Post by merlinus on 2009-07-02
You can resize the windows partition during installation, but do not make the partition too small.  Be sure to defrag several times beforehand.

As long as you do not choose to use entire disk, the windows partition will be left alone.

---

### Post by Ulfgeir on 2009-07-02
I'm new to Ubuntu as well, and experienced this same issue upon installation.  I went through and chose the "side by side" installation option, so that I could keep Vista for certain applications I have yet to find Open Source replacements for.  However, upon my first boot into Ubuntu, I was prompted to download updates and then subsequently informed that I lacked the disc space to proceed.
 
What I missed the first time through, but caught upon my second installation attempt, is that when you're choosing partition options, there's a slider bar further down the page that let's you adjust how much disc space Ubuntu is going to utilize.  By default, it seems to be pushed all the way over, assigning itself only about 2.3 GB.  This seems to be regardless of how much space is available, as I had insured a full 110 GB of free disc space was open before attempting my install.
 
So when you attempt your second go-through, put your check in "side by side" to keep Windows intact for a dual-boot, and then look further down the page and pull that slider over to adjust the space used by Ubuntu.  That fixed it for me.

---

### Post by raymondh on 2009-07-02
> **velopimp said:**
> i guess i figured ubuntu would help itself to a decent partition automatically (i chose the automatic install).....

not the case....

so if i have this correct, what i should do is resize the windows partition and reinstall ubuntu?  

can that be done without reformatting?

also, if i were to simply try to reinstall ubuntu, could i just resize there?

thank you so much for taking time to help

Hi,

Some reading materials for reference:

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

**If you decide to re-install by deleting the existing ubuntu** :

-back-up your files first and save elsewhere (just in case)

-take the moment to defrag windows first.  

-Then, boot into your ubuntu liveCD and access gparted (system > admin > partition editor) to delete the ubuntu partition (swap, root, extended) to leave it unallocated.  

-Then, downsize/resize the windows partition which should enlarge the unallocated partition to your desired specifications.  

See the above-mentioned links for reference. 

While you have not yet re-installed Ubuntu, you may want to consider having a separate /home partition.  Here are some links for your reference:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[http://ubuntuforums.org/showthread.php?t=1175277](http://ubuntuforums.org/showthread.php?t=1175277)

The second link is an ubuntu thread where Didius Falco (thanks Didius) was assisting the OP in creating a separate /home partition.  It starts in post 6.

Do post back if you need assistance or encounter 'challenges'.

Good luck.

---

### Post by presence1960 on 2009-07-02
> Some reading materials for reference: By raymondhenson! +1

How many times have we seen this scenario in here with exactly 2.3 GB of space for a root (/) partition. As raymondhenson so adequately posted - read! Installing a new OS from scratch is no task to be rushed into. One should read and familiarize themselves with exactly what it is they are going attempt to do. preparation is essential, especially if one has never installed an OS before. Restoring Windows from a recovery CD/DVD or recovery partition does not count as installing an OS because the partitioning and installation of software & drivers is done by the disk. Now if you have ever installed Windows from an installation CD/DVD you know what I am talking about- that is really installing an OS.

I don't say this to be mean or sound hard, but you really need to know what you are going to do before you do it. raymondhenson gave you some good links to read. here is another: [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)  -for a pdf Ubuntu Pocket Guide which has a great step by step on Ubuntu installation - and much more!

---

