---
title: "swap part. - necessary? what type partition"
date: 2005-12-29
forum: Installation &amp; Upgrades
---

### Post by HarryMangurian on 2005-12-29
How important is it to have a swap partition ?

Partition magic allows you to create Linux partition but does not mention Linux swap partition as a type.   I do not want to use gparted because it keeps making the swap partition a primary which I do not want.

Anyone know what type to use ?

---

### Post by Pablo_Escobar on 2005-12-29
Swap partition is important. I won't point out the reason for creating one, but have in mind that when Your PC is out of RAM it'll use swap, and it's advised by everybody to use it,

Partition Magic -> If my memory serves me right (no Win for some time) there is an option to create Linux swap partition. It'll do.

---

### Post by psusi on 2005-12-29
Don't use partition magic.  Just install ubuntu and if you already have windows installed, it will  offer to resize it to make space, and install to the free space.  

If you have already resized with partition magic, then just leave the free space unpartitioned and install ubuntu, let it create the partitions.

---

### Post by stuporglue on 2005-12-29
Or just leave a big chunk of free space and tell the Ubuntu installer to use free space. It'll partition the free space into the right partitions, including swap.

---

### Post by Luke771 on 2005-12-29
I did my install with a Partition Magic bootable CD and it went nice and smooth, you can make Linux ext3 partitions and Linux swap partitions with it.
The Ubuntu installer comes with a built-in partioner, fairly easy to use if you want to configure a Linux-only system, you get menus and multiple choices, but I still think that it is much easier to set up a dual boot system with a full graphic interface as in Partition Magic, the only probem is that it is commercial software, which means that you have to pay for it, if you have moral problems about file sharing in general and BitTorrent in particular ;-)
I heard that it is available a free Linux alternative, (both "free" as in "free speech" *and* as in "free beer"), sorry I don't rememer the name at the moment.
You can actually use only the Ubuntu installer and still set  everything up perfectly, all I'm saying is that it gets easier with Partition Magic.
And yes, you do need a swap partition; the patition type is called... well, Linux Swap Partition, and you can make one of those using Partition Magic or the paritioner included in the Ubuntu install.

My dual boot system was set up like this:
- Partition the drive With Parition Magic, and make
. . -first partition: PRIMARY NTFS 7,5 GB (Windows) and set it active
. . -second partition: PRIMARY Linux ext3 5GB (Ubuntu)
. . - third: 2,2 Linux Swap, logical
. . -fourth:  FAT32 logical, as big as the remaining space on the drive. (you can leave out the last 2GB, the reason why to do this comes in a minute...) I think this is a good setup is because FAT32 is accessible och writable both by Linux and Windows, in this partition you can store your files, while in the first two you will install Windows Ubuntu and the respective applications.
. . -fifth partition (optional) a 2 GB NTFS logical partition, exclusively for the Windows Page File (in this case you can make the first NTFS (Windows) partition 6 GB instead of 7,5), then set (in win of course) the page file to be about 1,6 GB both as initial size AND max size on this last partition and NO page file in the main Win partition... ok, more on that on a windows forum :-)

Install Windows first.

Then boot from the Ubuntu CD and follow the on screen instructuions.
When the partitioner comes, choose "manually edit".
Make the mount point for the windows partition /windows.
Make the second partition active and bootable, the mount point being / (the first ont the top in the list of options) and format it.
Leave the swap partition alone, it will be configured automatically.
Make the mount point of the FAT32 partition /media/whatever/  
I mean, you can make up the second part of the name, in this exemle "whatever" and that will the only part showing up on your desktop;
Making the first part /media/ will automatically mount your FAT32 file storage partition as fully accessible read/write (mine as mounted as /media/hda6/ which by the way is the default mount point, and shows up on my desktop as "hda6") you don't need to format it now.
You dont need to mount the NTFS windows paging partition (if you made one), choose Do Not Mount in the mount point menu; you will get an error message saying that partition 8 does not have a mount point, but that was exactly what we wanted to do (you dont need access to a windows page file from  Linux, do you?)
When it asks "do you want to install GRUB in the main boot sector?", make it a big fat NO I DONT and install GRUB in hd0,1 instead (that means the second partition of the first hard disk, the count begins from zero in both cases)
I know you didnt ask for no detailed installing how-tos, but I posted this one anyway mostly because of the part about having a big FAT32 partition and relatively small partition for Linux and Windows.
I noticed that a lot of people have more or less half the drive for windows,  half for Linux, and sometimes a little FAT32 partition for exchanging information between the two OS, which I think is not the best solution.
In my opinion it is much better to have one Wnidows-OS-and-installed programs-only partition; one Linux-OS-and-Installed-programs-only partition, and one big FAT32 file stoage partition accessible and writable by both, we can call it a "Big Fat 32" partition :-) 
On my system, I have a also windows-paging file-only partition, but that is not intresting in an Ubuntu forum.
And that's all, I hope I helped someone; I noticed that a lot of people worries about the difficulties of installing and runnig Linux, and is a little afraid of doing The Switch, but when I tried it was much easier than I thought, all those myths about Linux being fore full-breed nerd highly trained compuer geeks must be some kind of Microsucks propaganda. It's actually easy to install and it runs much faster and smoother than Windows (AND no one tries to make you pay for everything you want to do, which saves you some cash both in software and prescription drugs)

---

