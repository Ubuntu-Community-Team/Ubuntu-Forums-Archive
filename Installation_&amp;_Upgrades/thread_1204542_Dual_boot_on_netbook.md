---
title: "Dual boot on netbook"
date: 2009-07-04
forum: Installation &amp; Upgrades
---

### Post by ckosloff on 2009-07-04
I have an Acer Aspire One netbook, this one is sort of on steroids because it has an 160 GB HDD and 1 GB RAM.
I already resized Windows partition to about 80 GB and would like to install Ubuntu Jaunty on the remaining free unallocated space.
I would like to install ext4 file system and format second partition with it.
Also, I need a boot manager at startup.
If I choose the third automated option I will be served with ext3 and am not sure if it will install the boot loader.
If choosing advanced I can select ext 4, but then I am presented with a screen that says "no root file system" defined and I cannot get past it.
Please explain procedure to a newbie.

---

### Post by earthpigg on 2009-07-04
did you set the mount point of your ubuntu partition to "/" ?

---

### Post by raymondh on 2009-07-04
> **ckosloff said:**
> I have an Acer Aspire One netbook, this one is sort of on steroids because it has an 160 GB HDD and 1 GB RAM.
I already resized Windows partition to about 80 GB and would like to install Ubuntu Jaunty on the remaining free unallocated space.
I would like to install ext4 file system and format second partition with it.
Also, I need a boot manager at startup.
If I choose the third automated option I will be served with ext3 and am not sure if it will install the boot loader.
If choosing advanced I can select ext 4, but then I am presented with a screen that says "no root file system" defined and I cannot get past it.
Please explain procedure to a newbie.

Bootloader ... GRUB will be installed automatically (unless you tell it to do otherwise)

1.  After you click MANUAL in the installer and FORWARD ... you will be presented with a window that says PREPARE PARTITIONS.
2.  On that windows, below the graph, you will see a table of partitions.  As you know, *do not touch NTFS or FAT* as that would be your windows (and the recovery) install.
3.  On the same table ... click on free space (where Ubuntu will reside)
-  Right click and select **NEW PARTITION**  _(We are going to make a swap partition)_
-  TYPE = **logical**  * New partition size = **1500 mb** (reco 1.5Gb) * location =** Beginnning** *  USE AS = **SWAP Area**....then click **OK**
-  You will still have free space left. *Note how much remaining in MB.*  When ready, Right click on it and select **NEW PARTITION **[U]( we will make Ubuntu root)
[/U]
* I am making a straight up install .... if you want to make a separate /home partition, it can still be done later with a tutorial from psychocats'

-  TYPE = **Primary**  * New partition size = **remaining space noted above after making swap** *  Location = **Beginning**  * USE AS = **Ext4**  * Mount point = **/ ** (that slash is root) ... then click OK

4.  **Review** the new graph showing your partitions and click **FORWARD** when ready to proceed.

Hope this helps, post back if you need assistance.

---

### Post by ckosloff on 2009-07-06
> **raymondhenson said:**
> 
-  Right click and select **NEW PARTITION**  _(We are going to make a swap partition)_
-  TYPE = **logical**  * New partition size = **1500 mb** (reco 1.5Gb) * location =** Beginnning** *  USE AS = **SWAP Area**....then click **OK**
-  TYPE = **Primary**  * New partition size = **remaining space noted above after making swap** *  Location = **Beginning**  * USE AS = **Ext4**  * Mount point = **/ ** (that slash is root) ... then click OK

Hi Ray,
Thanks for helping me out.
I don't understand New partition size = 1500 mb (reco 1.5 Gb).
Why should it be 1500 mb? I have 1 GB memory.
What is reco?
I will follow your instructions to the letter, have already read Gina's reference.
Please post a link to psychocats' tutorial.
I want to get into Linux seriously, but there are many things I don't fully understand yet.
Please note that the Windows partition is at the beginning now, occupying approx. 80 GB.
I don't have a recovery partition, have already wiped out all the commercial crap they sold me with the computer and installed a clean OS.
My plan is to resize the Windows partition to approx. 50 GB, then install Ubuntu in another 50 GB, and keep a third NTFS partition of approx. 50GB for the work I would output, and that both systems could access.
I suppose that with this plan I will end up with 4 partitions, one of them being the swap partition, right?
Thanks again.

---

### Post by oldfred on 2009-07-07
I believe Raymond is just telling you that you have to input in mb for the partitions so to get 1.5 gb you enter 1500mb. 

Swap used to be 2x memory back when memory was 256 or 512mb. Now with 1 or more gigs of memory you may not need swap for regular use unless you run several very large applications, but if it is a portable and you will use hibernation you need at least memory plus something to allow all of memory into hibernation. Swap of 1500mb is a good choice since you have 160gb hard drive and space should be available anyway.

---

### Post by raymondh on 2009-07-07
As Oldfred stated (thanks, OldFred :)) ...

The partitioner will require you to input a size in mb.  Since I was recommending 1.5GB for SWAP, that is equivalent to 1500 mb.  If you don't plan to hibernate or suspend that much, 1GB (or 1000 mb) is good enough.

Ok, let's talk about partitions.  You/Us .. we have a 4 partition limit per disc.  Whether they be primary or extended.  the nice thing about an EXTENDED partition is our ability to create "logical" partitions inside it, for as long as the OS will allow.  Think of an Extended partition as a closet and a logical partition as a drawer inside that closet.  As it stands, you have (and desire*)

WINDOWS
UBUNTU*
COMMON STORAGE*

Here's a link to a thread where the OP created partitions prior to installing and then just chose Manual (on the actual install) and edited.  If you'll notice, your plans of having a common storage are similar to the OP's in that thread.  Some differences;  1. the OP there was using XP while you are using Vista which will shrink/resize the windows partition.  2. Another difference is the OP there chose to create a separate /home from the beginning.  Kindly read.

[http://ubuntuforums.org/showthread.php?t=1202483](http://ubuntuforums.org/showthread.php?t=1202483)

Here is the link for psychocats'

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

You are on the right track in researching and reading prior to installing.  Preparation is the key to minimizing hair-pulling adventures in dual-booting/installation.  Some reference links to browse at:

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

Good luck.  Back up your files first.  Defrag Vista next.  Try the liveCD after (checkdisk, check hash, see how it reacts to your system specs' and hardware) and when ready, Shrink Vista using it's own disk management tool and then.... install.

Post back if you need further clarification.

---

### Post by ckosloff on 2009-07-12
Guys,
Thank you so much for the great support.
I already partitioned disk like so:
Windows (approx. 50 GB)
swap (1.5 GB)
Ubuntu (approx. 50GB)
Data (approx. 50 GB), this is a shared NTFS partition, which I formatted under Windows, storage partition.
Everything is working fine, except for some minor glitches that I still have to iron out, like my wireless not working under Ubuntu, but if I still encounter problems will post in a different thread.
Writing from Ubuntu now, so it works!
Thanks again.

---

### Post by raymondh on 2009-07-12
> **ckosloff said:**
> Guys,
Thank you so much for the great support.
I already partitioned disk like so:
Windows (approx. 50 GB)
swap (1.5 GB)
Ubuntu (approx. 50GB)
Data (approx. 50 GB), this is a shared NTFS partition, which I formatted under Windows, storage partition.
Everything is working fine, except for some minor glitches that I still have to iron out, like my wireless not working under Ubuntu, but if I still encounter problems will post in a different thread.
Writing from Ubuntu now, so it works!
Thanks again.

CONGRTATULATIONS =D>

Happy Ubuntu-ing.

---

