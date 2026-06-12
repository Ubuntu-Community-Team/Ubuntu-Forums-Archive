---
title: "How do you dual boot?"
date: 2009-08-22
forum: Installation &amp; Upgrades
---

### Post by Maheriano on 2009-08-22
I'm very surprised a search turned up no guides for this, just pages and pages of people with failed attempts. Last year I gave my brother a laptop with Ubuntu on it, and today I'm finally convincing him to dual boot his desktop with Vista so I'm getting there! He just formatted it and installed Vista today so now how would he go about dual booting Ubuntu on it as well? Is there maybe a guide I can follow?

---

### Post by nhanquy on 2009-08-22
To be able to do dual boot (tripple boot,...) you have to have space left in the disk. If the disk has been partitioned fully then you have to shrink the windows partition to make space for Ubuntu.

Shrink partititions:
1. Boot the Ubuntu liveCD
2. Use "Partition Editor" to shrink to Windows partition (Just select it then "resize" then "apply")
3. Live some space as unallocated (Ubuntu will get into this space).
4. Boot PC again to check you still can get into your Windows OS.

Load Ubuntu to dual boot:
1. Boot the Ubuntu liveCD
2. Install Ubuntu
3. Reboot - Done!

How simple would that be?

---

### Post by Maheriano on 2009-08-22
Oh, it puts Windows into Grub on its own? I didn't know that.

---

### Post by stlsaint on 2009-08-22
This is assuming that you only have one hdd inside your system...you didnt give much info to go off of!  

assuming you already have windows...go thru windows disk management and allocate a partition for ubuntu it doesnt matter what format you use but go with ntfs then go as follows....

1. download and burn ubuntu to disk
2. boot to cd and click on isntall
3. go thru defaults until you get to partition manager
4. THIS IS VITAL....SELECT MANUAL WHEN YOU GET TO WHERE TO INSTALL...DO NOT INSTALL TO ENTIRE DISK....DO NOT OR YOU WILL ERASE WINDOWS!!
5. now when you select manual you are going to need to make two seperate partitions...one for (/), and one for (swap)
6. make the swap partition twice the size of your ram on your system...rule of thumb! 
7. make your / the rest of the partition... and format it using ext3...
8. from there isntall as normal and its smooth sailing!!

---

### Post by lisati on 2009-08-22
There is some potentially useful information here: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

**VERY IMPORTANT**
[LIST]
[*]Make backups of your important data. As much as we don't like to admit it, sometimes things go wrong, and it can be very useful to have a way of recovering useful and important data.
[*]Make a backup of any recovery partitions on your system. There are a number of ways of doing this - if you're in luck, your copy of Windows will have suitable software already installed.
[*]Plan changes to your system carefully.
[/LIST]

**Useful Reading**
[LIST]
[*][www.ubuntuforums.org](www.ubuntuforums.org)
[*][help.ubuntu.com]("http://help.ubuntu.com")
[/LIST]

**TIP**

 Some people prefer to use Google to search for answers. You can put the words **site:ubuntuforums.org** after the words you are searching for in Google's search box to limit results to the forums.

---

### Post by Bartender on 2009-08-22
There are plenty of guides.  The problem is there are too many variables to just write one or two.  If everyone who did it successfully wrote back with a concise description it would be great, but you mostly see posts from people who need help...

_THE BASICS_

*If* you have one HDD in the PC, and *if* it already has Windows, and *if* there's at least 50 or 60 GB of free space, and *if* the PC didn't come with 3 or 4 primary partitions right from the factory, and *if* the operator has at least a rough concept of primary vs. extended and logical partitions, mounting, Windows partition terminology, Linux partition terminology, GRUB terminology, etc. and *if* the operator has an Ubuntu install CD that was written properly, everything can go pretty smoothly.

I wouldn't do an install without a GParted LiveCD, but that's just me.  And I don't like letting Ubuntu install automatically, but again that's my preference.

Beginning to see now why there isn't a one-size-fits-all guide?

---

### Post by presence1960 on 2009-08-22
I would use Vista's disk management utilty to shrink it's partition after defragging Vista at least once or twice. There are a lot of members in here who have had vista problems after shrinking Vista's partition with a third party partitioner such as Ubuntu live Cd's gparted, Gparted Live CD or parted magic. better to be safe and err on the side of caution especially since it isn't your machine. Back up data, defrag, shrink Vista's partition with the disk management utility inside windows.

Then install using the Ubuntu Live CD by choosing use the largest contiguous free space. This will install Ubuntu to the unallocated space you created by shrinking Vista's partition.

I am like Bartender, I always set my partition scheme up prior then use the manual install. I gave you what I consider the easiest method to install Ubuntu with Vista already installed.

---

### Post by Bartender on 2009-08-23
Looks like the OP went away.  I hope he's not hip-deep in Ubuntu alligators.

Hey, Maheriano, I should have mentioned this but missed it in your first thread.  If you've just reinstalled Vista, then there aren't any worries about losing personal data, right?

I want to mention a different method, one that really appeals to me because it's so elegant.  It would involve reinstalling Vista again. 

If you're going to install Windows fresh anyway, use a GParted LiveCD (or an Ubuntu LiveCD) to create an NTFS partition FIRST.  The trick is, you don't create one big NTFS partition.  You go in with your partitioner CD of choice and delete all partitions.  Then you decide how much room you're going to give to Windows, and create a primary partition of that size, formatted as NTFS .  Either leave the rest of the HDD unallocated, or better yet, create an extended partition out of the rest of the HDD.  You can leave the space inside unallocated or if you have a plan you can format accordingly.

When you pop the Windows install CD in, it only recognizes the NTFS partition and installs to that area.  

This method is a wonderful workaround that eliminates the hassles which arise when Windows plunks data way out in the middle of the HDD and doesn't want to move over.

---

### Post by raymondh on 2009-08-23
> **Bartender said:**
> 

This method is a wonderful workaround that eliminates the hassles which arise when Windows plunks data way out in the middle of the HDD and doesn't want to move over.

Nice tip ... that forces all important files as close as possible to the front.  And from there, just enlarge the partition.  Nice tip :)

---

