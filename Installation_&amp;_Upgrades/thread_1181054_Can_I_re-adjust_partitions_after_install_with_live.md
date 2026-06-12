---
title: "Can I re-adjust partitions after install with liveCD"
date: 2009-06-07
forum: Installation &amp; Upgrades
---

### Post by pdr001 on 2009-06-07
I installed 9,04, dual-boot,on a 100 gig drive Thinkpad z61p. I accepted the setup partitioning, which gave me a 92.5g ntfs, 2.3g ext3, 180m swap and a 4.8 fat32. Although, Ubuntu loads and I can use some programs, None of my settings get saved and updates will not download because of insufficient space.
Can I just go through the installation process again with the Live CD and re-adjust the partitions to give me  larger ext3 and swap . Hopefully this would solve my problems. Thanks.

---

### Post by Anger 2 on 2009-06-07
You might find this guide helpful.
[http://www.linuxnewbieguide.org/content/paritioning-disk](http://www.linuxnewbieguide.org/content/paritioning-disk)

---

### Post by Therion on 2009-06-07
It can be done, yes.  However, you'd be better off using a gParted LiveCD instead of an install CD, in my opinion:

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

The whole caveat about making backups before playing with partitions... I don't need to go on about that, do I?  Of course not.

---

### Post by merlinus on 2009-06-07
You cannot do anything with a mounted partition, so using gparted or ubuntu live disks should work.  You should give at least 5G to /, and more if you will be adding a lot of apps and such.

Are you also running windows?  If not, why so much space for ntfs?

---

### Post by pdr001 on 2009-06-07
Thanks for your responses, I did a full hard drive backup prior to installing and it would not be a disaster if I had to reinstall XP.  Will the install CD recognize I already have 9.04 installed and only perform the manual repartition or will it go through the complete install. I accepted the install partition setup Live CD provided me and did not manually set it. I'm a newbie and thought the setup program would give me the correct partitioning. I am also running windows XP.

---

### Post by merlinus on 2009-06-07
You do not want to reinstall if you are wanting to resize existing partitions.  If you select try without changing anything from the opening menu, you will have a version of ubuntu running in ram.

You can then select System/Administration/Partition Editor and eidt your existing partitions with that.

However, if you are wanting to resize windows as well, then delete temp and other unneeded files and defrag that partition first, from within windows.

---

### Post by pdr001 on 2009-06-07
I resized My windows partition t0 50g using GParted with live cd and XP still boots. Now I have 48g of unallocated space under /dev/sda1. How do I resize /dev/sda5 and 6 (ext3 and swap) to utilize this space in GParted or do I have to do a complete re-install? This space does not appear when selecting resize/move for ext3. Thanks

---

### Post by merlinus on 2009-06-07
Post a screenshot of what you are viewing in gparted.

---

### Post by pdr001 on 2009-06-07
[IMG]file:///tmp/moz-screenshot-1.jpg[/IMG][IMG]file:///tmp/moz-screenshot-2.jpg[/IMG]
Not sure if sreenshot is visible. never did it before I copied ti clip and pasted int msg
. also uploaded
[IMG]file:///home/ubuntu/Desktop/Screenshot--dev-sda%2520-%2520GParted.png[/IMG]

---

### Post by merlinus on 2009-06-07
You cannot paste the image into your post.  Use the upload feature, and browse to where the graphic is located on your computer.  Then I believe you have to press the upload button.

---

### Post by pdr001 on 2009-06-07
[ATTACH]116789[/ATTACH]
ok

---

### Post by merlinus on 2009-06-07
Use gparted live or ubuntu live cd to resize your partitions.  Delete swap, which for some reason is humongous.  Then use the unallocated space for swap, and add the former swap space to sda5.

---

### Post by pdr001 on 2009-06-07
The unallocated space (37g) does not show up in the resize/move window for ext3. The max. size is 2385m. Also the swap is 172.54 m. I thought it should be be similar to one's installed Ram, which is 1.5g.

---

### Post by merlinus on 2009-06-07
My bad re: swap.  I read G instead of M.

The problem may be that the unallocated space is in what used to be a primary partition, and the rest are within an extended partition.

Did you try the gparted live cd?  It may have better features than the one on the ubuntu disk.

Failing that, the best alternative may be to reinstall ubuntu, this time using the unallocated space as /.

---

### Post by Anger 2 on 2009-06-08
You could use Disk Management in XP or Gparted to delete the existing Linux partitions and then reinstall Linux on the unallocated space following the manual proceedure.You then have the choise of the partition sizes.

---

### Post by Mark Phelps on 2009-06-09
> **pdr001 said:**
> The unallocated space (37g) does not show up in the resize/move window for ext3.

That's because you have to resize the Extended partition first, to make room for then resizing the Ext3 partition inside of it.

---

### Post by pdr001 on 2009-06-09
I ended up deleting all linux partitions. I am using the Live CD ti reinstall and manually set partitions. Using the partitioning guidelines &quot;The root partition / must always physically contain /etc, /bin, /sbin, /lib and /dev, otherwise you won't be able to boot. Typically 150–250MB is needed for the root partition.&quot; I entered, 250 in new partition size,selected,ext3file sys,and mount point /. After setting up other partitions the program warns me, the / is to small. What am I not getting?  I selected free space and then selected "New partition Table"  Device        Type        Size     Used /dev/sda   /dev/sda1    ntfs        52427 MB   25900 MB   free space               42807   /dev/sda2    fat32       4791       4002

---

### Post by merlinus on 2009-06-09
/ needs far more than you gave to it.  Depending upon free space and how much software you plan to install, 7-10G is good.

---

### Post by pdr001 on 2009-06-09
I'm trying to follow the guidelines  in "Umbuntu Documentation" [https://help.ubuntu.com/9.04/installation-guide/i386/directory-tree.html](https://help.ubuntu.com/9.04/installation-guide/i386/directory-tree.html) and set up accordingly.  The following is a list of important considerations regarding directories and partitions. Note that disk usage varies widely given system configuration and specific usage patterns. The recommendations here are general guidelines and provide a starting point for partitioning.      *        The root partition / must always physically contain /etc, /bin, /sbin, /lib and /dev, otherwise you won't be able to boot. Typically 150–250MB is needed for the root partition.     *        /usr: contains all user programs (/usr/bin), libraries (/usr/lib), documentation (/usr/share/doc), etc. This is the part of the file system that generally takes up most space. You should provide at least 500MB of disk space. This amount should be increased depending on the number and type of packages you plan to install. A standard Ubuntu desktop requires a minimum of 1.5GB here. A generous workstation or server installation should allow 4–6GB.     *        /var: variable data like news articles, e-mails, web sites, databases, the packaging system cache, etc. will be placed under this directory. The size of this directory depends greatly on the usage of your system, but for most people will be dictated by the package management tool's overhead. If you are going to do a full installation of just about everything Ubuntu has to offer, all in one session, setting aside 2 or 3 GB of space for /var should be sufficient. If you are going to install in pieces (that is to say, install services and utilities, followed by text stuff, then X, ...), you can get away with 300–500 MB. If hard drive space is at a premium and you don't plan on doing major system updates, you can get by with as little as 30 or 40 MB.     *        /tmp: temporary data created by programs will most likely go in this directory. 40–100MB should usually be enough. Some applications — including archive manipulators, CD/DVD authoring tools, and multimedia software — may use /tmp to temporarily store image files. If you plan to use such applications, you should adjust the space available in /tmp accordingly.     *        /home: every user will put his personal data into a subdirectory of this directory. Its size depends on how many users will be using the system and what files are to be stored in their directories. Depending on your planned usage you should reserve about 100MB for each user, but adapt this value to your needs. Reserve a lot more space if you plan to save a lot of multimedia files (pictures, MP3, movies) in your home directory.  Should I use another scheme?

---

### Post by merlinus on 2009-06-09
It is much simpler than this.  In general, a good setup for ubuntu is 3 partitions, /, /home and swap.  Obviously it all depends upon how much hdd space is available.

If you search through various threads on the forum, you will get a sense of what folks recommend. 

You can get by with smaller partitions, but when you run out of space, unless you can free up some and resize your partitions, you are basically screwed.  Of course you can always buy a bigger hd and reinstall.

When I had a 40G hdd and 1.5G ram, I still used 10G for /, 1.5 swap, and the rest for /home.

Now that I have a 500G hdd and 4G ram, I use 14G /, 1.4G swap. 18G /home, and the rest for a huge /data partition where I store documents, digital photos, and such.

YMMV.

---

### Post by pdr001 on 2009-06-11
Thanks for your help. I set my partitions similar to yours and everything works fine.
 []("http://ubuntuforums.org/forumdisplay.php?f=333&daysprune=-1&order=desc&sort=voteavg")  		[]("http://ubuntuforums.org/forumdisplay.php?f=333&daysprune=-1&order=asc&sort=title")[]("http://ubuntuforums.org/forumdisplay.php?f=333&daysprune=-1&order=asc&sort=postusername")[]("http://ubuntuforums.org/forumdisplay.php?f=333&daysprune=-1&order=desc&sort=lastpost")[]("http://ubuntuforums.org/forumdisplay.php?f=333&daysprune=-1&order=desc&sort=replycount")[]("http://ubuntuforums.org/forumdisplay.php?f=333&daysprune=-1&order=desc&sort=views")I  thought I was following official guidelines for partitioning. The page I referenced is on this site. Unless I misinterpeted the information, it seems it should be corrected. As a newbie trying to learn a new OS this created much confusion.

---

### Post by merlinus on 2009-06-12
AFAIK there is no "official guide" for partition sizes, as much depends upon use and hdd space.

But there are always knowledgeable and experienced folks on the forums who will help.

Glad it worked out, and post back if you run into difficulties.

Happy ubuntuing...

---

