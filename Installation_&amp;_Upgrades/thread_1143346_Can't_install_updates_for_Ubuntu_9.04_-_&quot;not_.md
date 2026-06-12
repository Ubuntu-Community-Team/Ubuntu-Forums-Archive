---
title: "Can't install updates for Ubuntu 9.04 - &quot;not enough space&quot; message"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by Unew on 2009-04-29
I'm a newbie @ Ubuntu / Linux and need a little help ... I can not install updates in Ubuntu 9.04.  When I run Update Manager to update the system, I receive an error message stating that there is not enough disk space.  I followed the directions in the error message, i.e., deleted the trash and ran the recommended command to cleanup the system, but neither step solved the disk space problem.  I am dual booting Ubuntu on my Vista laptop.  When I installed Ubuntu, I allowed the Ubunutu installer to automatically create the Ubuntu partitions (2.33 GB / 173 MB).  Based on the error, it appears the Ubuntu installer did not create enough disk space for the Ubuntu operating system.  I did not manually create the partition sizes.  The laptop hard drive (160GB) has plenty of free space for both Vista & Ubuntu.  How do I solve the problem I'm having in Ubuntu?  How do I "resize" the partition for Ubuntu so I can update the system?  Since I'm new @ Linux, I'd really appreciate the clearest and most detailed instructions.  So far, I like Ubuntu, but I have to be able to update it to use it.  Thanks in advance for your help and time.

---

### Post by lindsay7 on 2009-04-29
Download Gparted from their web site and burn the ISO image to a cd or dvd. It will boot up when you start your computer with the disk in your drive. You can repartition the drive with it. The site has all the support info you need.

---

### Post by Partyboi2 on 2009-04-29
Hi, if you have not already got unallocated space available on the hard drive to increase Ubuntu, boot into Vista and use the resize tool to shrink down the Vista partition so you are left with unallocated space.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
Then boot a ubuntu live cd and open gparted (System>Admin>Partition Editor) and select ubuntu partition that you are wanting to increase and right click and make sure that it is unmounted. Then right click again on it and choose resize/move and increase the size of the partition to use the unallocated space.

---

### Post by Unew on 2009-04-29
Thanks for the replies, however, I'm still stuck.  I used the partition program in Vista to create 5GB of unallocated space.  Then I ran Gparted from the Ubuntu 9.04 Live-CD with the goal of using the 5GB unallocated space to expand my Ubuntu partition.  That's where I'm stuck.  I'm not able to use Gparted to increase the size of the Ubuntu partion.  I can see the 5GB of allocated space, but I don't know how to move it or otherwise get it into the Ubuntu partition.  The current size of the Ubuntu partition is 2.33GB, and Gparted says there is 0 free space preceding and 0 free space following (min. size = 1.93GB & max. size = 2.33GB).  Bottomline:  How do I resize the partition using the 5GB of unallocated space? I read the help file for Gparted, and note that it says to grow or move a partition, unallocated space must be available adjacent to the partition.  The 5GB space is available but it is NOT adjacent to the Ubuntu partition that needs to be increased in size.  How do I move the unallocated space adjacent to the Ubuntu partition.  I must be missing a step or something, because I can't figure this out.  Please help!  Thanks much.

---

### Post by lindsay7 on 2009-04-30
If you used the Ubuntu live cd to run Gparted, you need to be sure to unmount the partitions that you want to work on. You can find the command to unmount in the tool bar or click on the partition and then right click on it and unmount it. This is why I suggested that you download and burn the Gparted live cd. When you use it all of the partitions will be unmounted.   You may need to make do some more shrinking and preallocating to do what you need.  If you have more trouble or questions, you may want to take a screen shot of the gparted drives and post so you can get some more help.

---

### Post by Partyboi2 on 2009-04-30
> **Unew said:**
> Thanks for the replies, however, I'm still stuck.  I used the partition program in Vista to create 5GB of unallocated space.  Then I ran Gparted from the Ubuntu 9.04 Live-CD with the goal of using the 5GB unallocated space to expand my Ubuntu partition.  That's where I'm stuck.  I'm not able to use Gparted to increase the size of the Ubuntu partion.  I can see the 5GB of allocated space, but I don't know how to move it or otherwise get it into the Ubuntu partition.  The current size of the Ubuntu partition is 2.33GB, and Gparted says there is 0 free space preceding and 0 free space following (min. size = 1.93GB & max. size = 2.33GB).  Bottomline:  How do I resize the partition using the 5GB of unallocated space? I read the help file for Gparted, and note that it says to grow or move a partition, unallocated space must be available adjacent to the partition.  The 5GB space is available but it is NOT adjacent to the Ubuntu partition that needs to be increased in size.  How do I move the unallocated space adjacent to the Ubuntu partition.  I must be missing a step or something, because I can't figure this out.  Please help!  Thanks much.
As already suggested can you post a screenshot of gparted (Applications>Accessories>Take Screenshot) so we have a better idea on where the unallocated space is located.

---

### Post by Unew on 2009-04-30
I've attached two screenshots from Gparted.  I believe the partitions /dev/sda 5 and /dev/sda6 are the active ones for my Ubuntu system.   Please note that I also have partitions /dev/sda7 and /dev/sda8, which I BELIEVE are related to a previous install of Ubuntu 9.04.   Before I posted my original help message to this forum, I attempted to solve my partition - "not enough space problem" by deleting unnecessary applications.  I made a mistake and deleted something necessary, which caused Ubuntu to fail to boot.  So I reinstalled Ubuntu, and new partitions were created.  The space problem wasn't solved, hence I posted my original help request.  I didn't delete the old partitions, because I was afraid I'd inadvertently destroy my dual boot settings.  

Two questions:

1. Based on the screen shots, can you tell me exactly what I need to do to resize / move the necessary partition(s)?

2.  Can you tell me how to properly delete the partitions from my original installation of Ubuntu 9.04?  If possible, I'd like to get rid of those unnecessary partitions, but I don't want to break Grub's dual boot of Vista / Ubuntu.

If you can, please address both questions.  Thanks again for all of your help!  I *really* appreciate the assistance!!!

---

### Post by lindsay7 on 2009-04-30
The first thing I would do is run defrag on your windows partition under windows (sda1).  Then I would use the live Gparted disk to shrink or resize this partition (sda1) by the amount you choose, it is large anyway. This will give you more unallocated space. Then delete the Ubuntu partitions that you do not need. Then increase partition sda3 to use that unallocated space.  Keep the swap partition the same size and increase the size of the ext partition that you end up keeping. If you are not sure which partitions are actually running your Ubuntu os. Go into the terminal and type

sudo gedit /boot/grub/menu.lst (that is the lower case letter l not #1).  That will show what is going on with the grub file and how it is booting.  Post this if you need help making sure what to delete.  When you run the sudo gedit command do not make any changes to that file.

Can anyone confirm that this is correct?

---

### Post by Unew on 2009-05-01
[SIZE=2]The problem regarding "not enough disk space problem to update my Ubuntu 9.04 system" has been solved.  I used gParted to expand the available space, and afterwards installed all the updates to my Ubuntu 9.04 system.  Thanks for your direction/  My system is now up to date.

I have one outstanding issue / question regarding the deletion of the two unnecessary partitions that were left over from my original installation of Ubuntu 9.04.  Can you confirm that I will not break my Vista / Ubuntu dual boot process if I simply use gParted to delete those unnecessary partitions?  Will grub generate any error messages regarding the deleted / missing partitions if I simply delete them?  Is there anything else I need to do to "clean-up" the boot.  I'm new at Linux and just want to be double sure before I delete the partitions  

I appreciate all your patience and assistance.[/SIZE]

---

### Post by lindsay7 on 2009-05-01
Try doing this, go to this web site and download the Boot info Script. This will download a file to you desktop.



[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)



Then type in terminal this command

sudo bash ~/Desktop/boot_info_script*.sh

This will creata a "results.txt" file on your destop. You can click on it to open it and then you can post it to the forum.

I would start a new thread or post to the forum with this info and ask for help to delete the extra un-needed partitions.  This way you will get a lot more help.  The results of the txt file should show which partitions are being used and which are not. I or someone else should be able to tell you which ones to delete and you should get more attention with a separate post on your new situation.

---

### Post by kharon on 2009-05-07
I have a 500 gig hdd and same problem,I have installed and uninstalled,ran live cd to partition,burned gparted iso have it on now,no joy.It appears that ubuntu installs in the free space at the end of my drive,and therefore has a limited space available.I defragged windows(XP) before I started and once since then due to changing partitions and so forth.I have XP installed on the first 30 gigs,had originally created two additional partitions during windows install hoping to have created a discernable partition table to view during ubuntu
install,I read a tutorial on gparted,downloaded and have attempted to resize and or partiton drive such that ubuntu installer would make the happy choice to install in all the extra space.The partiton manager in ubuntu install gives you several options,install side by side giving boot option,use entire disc,largest free space,manual,I have installed to whole drive that works just not ready for that yet,the problem seems to be if you install side by side the 2.33 gig is what I get,I have not been able to partition manually or to resize to resolve,extra space or side by side 2.33 gig.Getting weary I hope ther is someone that can help.:confused:

---

### Post by magicvn on 2009-07-22
I have a same problem, firstly, I have 2,36 GB for Ubuntu, and I want more 5GB unallocated space.
I used GParted to mix Ubuntu space with  unallocated space, and In Gparted my /dev/sda6 reached 7,36 GB (In the first picture), however, when I download some files to my desktop, the system has still warned "not enough space", and when I use the df command in Terminal, sda6 has only showed 2,3 GB (In the second picture).

Please let me how to solve, (My English is not well:))

Thanks in advance!

---

### Post by magicvn on 2009-07-22
In addition, I unable to read content on sda8 and sda5 (because of this some operations may be unavailable ), How can I use it..

---

### Post by Partyboi2 on 2009-07-23
> **magicvn said:**
> In addition, I unable to read content on sda8 and sda5 (because of this some operations may be unavailable ), How can I use it..
You will need to increase the size of your Ubuntu partition (sda6) as you only have a 154mb of space left.  If you have the room you can either shrink down sda5 or sda8 and then increase the size of sda6.
When you work on partitions they can not be mounted so use a ubuntu live cd and make sure they are unmounted before working on them (right click on the partition and choose to unmount)

---

