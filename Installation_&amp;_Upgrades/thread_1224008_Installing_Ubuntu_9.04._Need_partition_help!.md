---
title: "Installing Ubuntu 9.04. Need partition help!"
date: 2009-07-26
forum: Installation &amp; Upgrades
---

### Post by Anotsu on 2009-07-26
Hello all! I downloaded Ubuntu 9.04 yesterday, mainly because I was interested in something new and shiny and because of its security against viruses. I tried it out on the live cd, and then did the Wubi install.

Now I'm thinking I would like to partition my harddrive in order to support the full speed of ubuntu, and still have windows xp. My idea is to be able to have windows XP in one smallish partition, Ubuntu in a small partition, and have a third partition for storing all of my files. I have no idea how to do this though!

Is that even possible? Have windows, ubuntu, and my files on seperate partitions, and have access to the same files whether I'm using Windows or Ubuntu?

I've looked around a lot for guides to help me partition my drive, but I can't find one that shows exactly what I see when running the partition tool included on the Live CD. I've seen some guides refer to a "slide-bar" that looks easy enough to use,  but when I boot up the installer from the disc I don't get one. Also, when I boot up the installer and get to the partition screen, I can't seem to create a new partition without completely erasing/formatting the entire disc. I still want to keep my windows xp and my files!

So what should I do here? I know absolutely nothing about Ubuntu and have just been fiddling with it for a couple of hours. I would like to learn more about it, but would really like to partition my drive so that if I get attached to it, I don't have to start over and install Ubuntu on a partition later on and lose everything. Any help would be appreciated!

Thanks!

---

### Post by running_rabbit07 on 2009-07-26
> **Anotsu said:**
> Hello all! I downloaded Ubuntu 9.04 yesterday, mainly because I was interested in something new and shiny and because of its security against viruses. I tried it out on the live cd, and then did the Wubi install.

Now I'm thinking I would like to partition my harddrive in order to support the full speed of ubuntu, and still have windows xp. My idea is to be able to have windows XP in one smallish partition, Ubuntu in a small partition, and have a third partition for storing all of my files. I have no idea how to do this though!

Is that even possible? Have windows, ubuntu, and my files on seperate partitions, and have access to the same files whether I'm using Windows or Ubuntu?

I've looked around a lot for guides to help me partition my drive, but I can't find one that shows exactly what I see when running the partition tool included on the Live CD. I've seen some guides refer to a "slide-bar" that looks easy enough to use,  but when I boot up the installer from the disc I don't get one. Also, when I boot up the installer and get to the partition screen, I can't seem to create a new partition without completely erasing/formatting the entire disc. I still want to keep my windows xp and my files!

So what should I do here? I know absolutely nothing about Ubuntu and have just been fiddling with it for a couple of hours. I would like to learn more about it, but would really like to partition my drive so that if I get attached to it, I don't have to start over and install Ubuntu on a partition later on and lose everything. Any help would be appreciated!

Thanks!

There is good news. If you need to store files where both systems can see them, you can either make a partition that is NTFS and both OSes will be able to read within. 

Or option 2 is you make a folder within your Windows system that you wnt to store files in as Ubuntu?Linux has the capability to read with your Windows partition but as far as I know, Windows can not read the EXT2, 3, or 4 files systems.

Let us know if you need help setting up your partitions.

---

### Post by Anotsu on 2009-07-26
Yes, I would love some help partitioning. As I mentioned in my other post, I don't see exactly the same things that the guides say I should when I looked at the partition.

---

### Post by running_rabbit07 on 2009-07-27
> **Anotsu said:**
> Yes, I would love some help partitioning. As I mentioned in my other post, I don't see exactly the same things that the guides say I should when I looked at the partition.

1. Have you backed up your system to external media as changing your partitions can cause loss of data?

2. Defragment your hard drive. This makes sure all your Windows files are at the front of your hard drive. (Helps prevent data loss.)

3. Have you decided if you want to save those files to which you want access from both operating systems in the Windows partition or in a separate partition? You need to know this so you can determine how big you want to keep your Windows partition.

4. If you want to make an extra NTFS partition for those files which you want to be able to open with both systems, you will need to make this partition from within Windows via Disk Management. You will have to use this utility to shrink your NTFS Primary partition so you can make room for the others. I have never done it, but I beleive this Disk Manager will allow you to make a new NTFS file partition for saving those shared files though I think you would be better off just keeping one NTFS partition and saving the shared files there.

5. Creating partitions for installing Ubuntu. You can make several different partitions with different uses but I only use 3. 

       a. I have one partition with the mount point*** /*** that is only 15 gigs. This partition will contain your Ubuntu OS files such as all your installed programs.

       b. A Swap partition that is 2-4 Gigs (recommended that you make this one 50% larger than the amount of RAM)

       c. The 3rd partition I use has the mount point ***/****home*. The size of this drive usually takes up the rest of your hard drive and stores saved files and all your settings.

(By using this 3 partition set up you have the capability of doing a clean install of the next release of Ubuntu or if you decide you want to back track to say 8.04LTS, or if you do like I have done and messed up some system files and need to reinstall the OS, you will still have all of your saved files and settings such as Firefox Bookmarks.)

This method works great for me, I have reinstalled my OS twice since setting up the /home partition and it made my life much easier.

I also recommend searching this [helpful site]("http://www.psychocats.net/ubuntucat/a-home-users-successful-migration-strategy-from-windows-to-ubuntu-2/") which is recommended by more than one of our forum moderators. [This page]("http://www.psychocats.net/ubuntu/installing") will run you through the install and has links for researching different partition methods. Though I have had no problems with EXT4, some people have so you may want to go with EXT3 to be safe. Feel free to study the psychocat site and going to [Ubuntu's]("https://help.ubuntu.com/9.04/index.html") site and reading their documentation.

If you have more questions feel free to ask. As you know there are lots of people here in the forum willing to help.

Edit: I have added a screenshot of my hard drive just so you can see what my partitions look like.

---

### Post by Anotsu on 2009-07-27
Well, I don't have a system backup, as I don't have an external drive or a large usb stick. I could use a DVD i guess, but I wouldn't know what would be good to put on it.

My computer says that I don't need to defragment. Should I do so anyway?

I think that the 3 partition system is the most appealing. That way if Windows gets a virus, I won't have to wipe my entire drive. What is the best way to do this? I looked for guides, and couldn't find any to help. Would Partition Magic be good to use? And how big should the partition for each OS be? Since I'll be putting all my files and media on a partition free of an OS, the smaller each other partition the better so I can have more storage space.

---

### Post by running_rabbit07 on 2009-07-27
Yeah, go ahead and defrag, while there may not be any fragmented files they are still scattered throughout the drive.

To resize you can go as mentioned to Disk Management via the control panel. Right-click on your hard drive and make it smaller so that you have room for the new partitions. You may even be able to do this via the install disk in the partitioner. 


After resizing the NTFS partition, you will then have an unallocated space on your hard drive. 

While using the install disk you can click open the unallocated space and then the new partition button. 

There will be a scroll button, click on it and set it to EXT3 then set the mount point to     /    then set the size to around 15000 Megabytes. Click OK.

Next, click the new partition button again. click on the scroller an click on Swap Area, set this partition to end of drive. Make it about 3000 Megabytes. Click OK.

Next, click the new partition one last time and set the scroller to EXT3 then set the mount to scroller at     /home     and use all the free space that is left. Click OK.

Click forward and install Ubuntu.

Happy Trails

---

### Post by Anotsu on 2009-07-27
When I click on Disk Defragmenter, it shows that I have a little bit of data at the very beginning, then a large white space followed by a large amount of data. Then another large white space followed by another large amount of data. It says that after defragmenting it will look exactly the same. How can I make those two white spaces between the data smaller when it is all in the one partition?

---

### Post by merlinus on 2009-07-27
It is probably the windows paging file.  You will need to disable it (look in System Tools), reboot, delete pagefile.sys, and then defrag several times.  You can reinstate it after partitioning.

Also be sure to empty all temp directories first.

---

### Post by running_rabbit07 on 2009-07-27
> **merlinus said:**
> It is probably the windows paging file.  You will need to disable it (look in System Tools), reboot, delete pagefile.sys, and then defrag several times.  You can reinstate it after partitioning.

Also be sure to empty all temp directories first.

+1 on removing temp files. You can use disk cleanup to clear all your temp files.

---

