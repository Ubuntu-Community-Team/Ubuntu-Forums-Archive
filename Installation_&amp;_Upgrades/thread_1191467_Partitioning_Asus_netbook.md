---
title: "Partitioning Asus netbook?"
date: 2009-06-19
forum: Installation &amp; Upgrades
---

### Post by RickyBobby on 2009-06-19
W00t!  Got Ubuntu running on my new netbook via USB thumbdrive.  

Unfortunately I had to install everything to one partition with no swap.  The Asus 160 GB drive came with four partitions already set up -- one big one for XP, another big one ("D" drive) on which I installed Ubuntu, and two smaller ones I think are for restoration (no dvd drive on this little thing).  

I don't really understand it but I've read there is a limit to how many ("primary"?) partitions you can install, and thus I couldn't install any more for swap or to separate root from /home without deleting others, which I'm not ready to do just yet.  I tried reducing the size of the linux partition hoping I could then divide it up but no luck, I'm guessing because I'm maxed out of partitions.

So is there any way to resize the Linux partition without messing up the others, or would I just have to take the plunge and overwrite the big XP partition.  I don't want to use Windows, but I just bought this thing and am not very experienced with Linux (a lifelong Mac user actually), so am proceeding cautiously.  Thanks for any thoughts!

---

### Post by anystupidname on 2009-06-19
Yes, if all partitions are primary, you maxed out. I have several suggestions. The easiest one (not necessarily the best) is to combine the two big partitions using this (can be done from *nix or winders) [http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=240127](http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=240127) (for example) and install Ubuntu into XP's NTFS partition. [http://wubi-installer.org/](http://wubi-installer.org/)

Another alternative, would be to create an extended partition in the place of the second big partition currently containing Ubuntu with multiple logical partitions in it. (you can have more partitions on the same disk that way) Be aware that *nix supports being installed in extended partitions, XP does NOT!

Both of the above assume you don't care about losing your current Ubuntu install.

I personally, would probably get rid of all factory partitions as you can reinstall Ubuntu and XP from USB thumb drive (with minimal foo) any time you need anyway. (but that is just me)

Cheers;)

---

### Post by nmaster on 2009-06-19
you should read these to start with.
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
  [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)
 
you can have 4 primary paritions.  If you want more, then you'll have to make what is called an extended parition and then use logical paritions with that.  I believe windows must be on a primary parition, but ubuntu doesn't have to be.  

Depending on how your paritions are organized you can expand the primary parition that ubuntu is on.  However, it sounds like your C drive has Windows.  I think you can only expand a parition if there is available space "to the right of it," that is, when using the LiveCD (in your case a USB drive).

I would suggest reinstalling Ubuntu on the C drive.  This will get rid of XP.  You could use the D drive as a parition for your home directory, but its up to you.

This isn't really a simple process if you've never done it before.  This might be due to my nerdiness, but I would suggest reading about it.  Searching "partitions" on this forum will return a lot of useful results. read as much as you can on partitioning and ubuntu in general. Using linux is not like using windows or mac. you should look at [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php) also.  read these forums.  it might seem like a steep learning curve, but after a few weeks you will learn a lot.  i definitely did and still am.

---

### Post by RickyBobby on 2009-06-19
Thanks to both of you for your comments; I know I have some reading to do.  As I have less than a week to return this netbook, I'll keep using what I have to fully test out the hardware, then probably I'll nuke the XP partition.  You're right, keeping that bootable thumbdrive should keep me safe for emergencies.  

Posted from my balcony, could not do that with the old iMac!

---

