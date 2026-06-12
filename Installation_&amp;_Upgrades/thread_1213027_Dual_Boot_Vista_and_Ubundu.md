---
title: "Dual Boot Vista and Ubundu"
date: 2009-07-14
forum: Installation &amp; Upgrades
---

### Post by krishnakumar75 on 2009-07-14
Hi 
 
I'm very new to the Linux world.
I do have laptop with following configuration,
 
OS: Windows Vista Ultimate pre-installed.
RAM: 1 GM
HDD : 120 GB (30 GB Free)
Partition: C: OS and Data
Partition D: (RECOVERY)
 
I can create a new partition from the free space (15GB) for ubundu installation.
 
I'm bit worried about,
a) Will the installation of ubundu on new partition (Say E:\) will have corrupt the Windoes Vista ?
 
b) How to removwe ubundu without corruoting the Windows Vista Instaaltion?
 
Plse help me
 
Thanks in Advance
 
KK

---

### Post by Mark Phelps on 2009-07-14
> **krishnakumar75 said:**
> Hi 
 
I'm very new to the Linux world.
I do have laptop with following configuration,
 
OS: Windows Vista Ultimate pre-installed.
RAM: 1 GM
HDD : 120 GB (30 GB Free)
Partition: C: OS and Data
Partition D: (RECOVERY)
 
I can create a new partition from the free space (15GB) for ubundu installation.

To install Ubuntu, you need Unallocated space, that is, space that is not inside an existing partition.  If this is what you're calling "free space", then you're OK; otherwise, you'll have to shrink an existing partition to create the unallocated space.  To shrink the Vista OS partition, be sure to use the Vista Disk Management utility, not the Ubuntu installer or GParted.  Using either of the latter runs the risk of corrupting the Vista OS so that it becomes unbootable.

> 
I'm bit worried about,
a) Will the installation of ubundu on new partition (Say E:\) will have corrupt the Windoes Vista ?

Your Ubuntu installation can not be inside an existing NTFS partition, so it will not corrupt Vista. However, it will overwrite the MBR so that it can use GRUB for booting into a menu that will contain entries for both Vista and Ubuntu.

The Ubuntu install will not use drive letters -- those are used in MS Windows.  
> 
b) How to remove ubuntu without corrupting the Windows Vista Installation?

You would remove it by (1) removing the Ubuntu partitions (best to do this by booting from a GParted LiveCD which you will have to download and burn from Distrowatch.com, and(2) restoring your Vista MBR by booting from a Vista DVD or from a Vista Recovery CD and doing Startup Repair.

---

### Post by raymondh on 2009-07-14
Another option for you is to try Ubuntu thru WUBI.  Note that Ubuntu will be installed INSIDE windows hence you will experience the same performance as you have for windows now.  What I mean is that if you find windows slow because it is fragmented ... so will be your Ubuntu.  Also, if your windows crashes, so does your Ubuntu.

The wubi install allows users to learn about Ubuntu while being within windows.  Later on, when you are ready, you can simply uninstall Ubuntu (wubi) like uninstalling a windows program ... through add/remove ... and then set up a true dual-boot and full-experience the speed, power and flexibility of Ubuntu/Linux.

For a wubi install:

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Now, if you want to dual-boot from the start, here are some references:

[https://help.ubuntu.com/community](https://help.ubuntu.com/community)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

Some notes about partitioning:

[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

Some tips whether you wubi or dual boot:

1.  Back up.  There are no gurantees.
2.  Defrag.
3.  Download the iso file, burn the image at a slow speed.
4.  Try the liveCD first and check for defects and hash and then......
5.  TRY without changing the system to see how it works with your system specs' & hardware.

Good luck.

---

### Post by merlinus on 2009-07-14
IMFFHO, recommending wubi is like telling people they have to install windows before linux.  Why not start folks off in the right direction immediately? 

With all of the illustrated guides to dual-booting and partitioning, this is like spoon-feeding people instead of allowing them to be independent and stand on their own feet.

And as you say, they then continue to be privy to all of the problems of windows.

If they want to try without buying, they can use the live cd.  After all, that's why it was created!

---

### Post by raymondh on 2009-07-14
> **merlinus said:**
> IMFFHO, recommending wubi is like telling people they have to install windows before linux.  Why not start folks off in the right direction immediately? 

With all of the illustrated guides to dual-booting and partitioning, this is like spoon-feeding people instead of allowing them to be independent and stand on their own feet.

And as you say, they then continue to be privy to all of the problems of windows.

If they want to try without buying, they can use the live cd.  After all, that's why it was created!

LOL.... as I agree because of my previous experience with WUBI installations.

As you and I know and advocate in many of our posts, the more options and research a new user makes, the less hair-pulling adventures :)

Ultimately, OP will have to decide what is best based on his comfort and skill level.... which we can never sense accurately in an initial post.

I agree with you though.  I prefer dual-booting (hence the reference links) or virtaulization.

:) Peace!

---

### Post by merlinus on 2009-07-14
I have learned tons more from what you call hair-pulling adventures than any other way.  Without risk, there is often little gain.

Most of what I have learned about computers, since I am self-taught, has been through creating learning opportunities, whether planned or by apparent accident, especially in terms of reinstalling operating systems, going underneath the hood, so to speak, to try and figure out solutions, and such.

As always, YMMV!

---

### Post by krishnakumar75 on 2009-08-02
Hi,
I have partioned my Laptop and created a new partion U: having 10GB space.
Using the Ubundu Install CD I installed on U:\ drive drive along with Vista in C: drive.
Use all default settings (Automatic SWAP, root regoin selection)
Also I tried with advanced settings by giving the SWAP and ROOT partion,..but both case result was same as below :-( 
 
After installation it prompsts for restart after removing the CD from the tray and click 'Enter'.
But unfortunately this stage in shows some black screen and some I/O errror.
 
After rebooting It directly loads the existing  Vista.
 
What is the problem exactly?...
 
Thanks
 
KK

---

### Post by Mark Phelps on 2009-08-02
> **krishnakumar75 said:**
> Hi,
I have partioned my Laptop and created a new partion U: having 10GB space.
I already said that Ubuntu does not use drive letters, so when you say you formatted a "U" drive, did you format it using NTFS?

If not, what file system format did you use?

---

### Post by krishnakumar75 on 2009-08-21
Hi all,
Finally I managed to install Ubundu on my XP.
I took the ext4 type.
But now when I'm trying to open any media files (Mounted on ) from ubundu,says there is no requried s/w available to play this.
What to do?.. from where I can get and install the media player? ( I have ubundu 9.04 CD)
 
thanks in advance,
 
Krishna

---

### Post by nhanquy on 2009-08-21
> **krishnakumar75 said:**
> Hi all,
Finally I managed to install Ubundu on my XP.
I took the ext4 type.
But now when I'm trying to open any media files (Mounted on ) from ubundu,says there is no requried s/w available to play this.
What to do?.. from where I can get and install the media player? ( I have ubundu 9.04 CD)
 
thanks in advance,
 
Krishna


get VLC:

```

sudo  apt-get install vlc

```

---

### Post by Bartender on 2009-08-21
The Ubuntu install CD does not give you a computer that will run proprietary software out of the box.  mp3's, DVD codecs, etc. can run on Ubuntu but you have to do some work.

Here's a very good place to start

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Also look into medibuntu.  

Between those two, you should be covered for almost any sort of media you want to watch or listen to.

---

