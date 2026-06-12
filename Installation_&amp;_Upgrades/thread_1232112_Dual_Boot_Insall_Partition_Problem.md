---
title: "Dual Boot Insall Partition Problem"
date: 2009-08-05
forum: Installation &amp; Upgrades
---

### Post by Balagast on 2009-08-05
I have a t43p (thinkpad) laptop with an 80gig HD.  I have Windows XP installed for using CAD and other software, but I wanted to have a dual boot of ubuntu 8.04 for everyday activities.

I got the part where I needed to create partitions and selected "manual" to edit the existing ntfs partition.  The problem is it will not allow me to edit the exisitng 80gig partition.  Also, the "used" column for the partition says unknown.

Do I need to use something else like gparted to partition this drive, or is there another issue here?

Thanks.

---

### Post by presence1960 on 2009-08-05
First back up all your data you don't want to lose. Althoiugh the partitioning process works extremely well remember murphy's law. Then defrag windows at least once or twice. Next boot the gparted Live CD and shrink XP's partition to create unallocated space for Ubuntu. Then create partitions for Ubuntu from the unallocated space. You need to think about what you want to do here. You will need a minimum of 2 partitions. One for Ubuntu (/) and one for swap. You can also create a NTFS or FAT32 partition for data shared between XP and Ubuntu. You can create a separate /home partition. There are other options also. Figure out how you want your partition scheme for ubuntu then create the partitions from the unallocated space. Note: you can do this from Ubuntu Live Cd also. Boot the Live Cd , choose "TRy ubuntu without any changes...", when the desktop loads go System > Administration > Partition Editor. I recommend gparted Live Cd because it is a more current version than the partition Editor on Ubuntu Live CD. Once partitions are created it is time to install.

At the Prepare disk space window choose manual. Highlight each partition you just created one at a time and click edit. Set parameters. Use as choose ext 3 or 4 for Ubuntu (/). Make sure you set the mount point as /.
Swap set use as to linux-swap. If you created a separate home partition do the same here and set mount point to /home. You need to nothing with an NTFS or FAT 32 partition at this point. Proceed with the install.

If that is too much for you choose Guided resize at the Prepare Disk space window of the installer. Then grab the right side of XP partition in the graphic and drag it to the left until you created your Ubuntu partition to the size you desire. The installer will do the rest for you.

---

### Post by ajgreeny on 2009-08-05
For XP, but not for vista, I would suggest you boot to the ubuntu live CD and use the partition editor in that (gparted) to shrink your winXP partition to whatever size you want, by moving the right hand end of it to the left, if you have not already done it.  make sure you have everything backed up and that you defrag a couple of times before you attempt any of this.

That will leave you with an unallocated area, the unknown bit in windows disk management, which is a pretty useless utility compared to gparted.  The windows disk management only recognises windows file systems, so don't worry about that unknown tag; it is unknown to windows but not gparted.

You can now use that unallocated area to install ubuntu, bychoosing Manual at the partitioning stage of the install.  You will need to select that area and make at least two partitions, / or root, and swap which I suggest should be about 1.5 - 2GB.  A separate /home is also worthwhile, making a reinstall or upgrade much easier to do in future.  Make / about 7 or 8GB, swap 1.5 - 2GB, and the rest as /home.

Have a look at [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) for more info.

---

### Post by Balagast on 2009-08-05
I should clarify a bit.  I was trying to edit the partition using the Ubuntu live CD partition editor.

I did try to defrag it a couple times.  I am currently running a diskchk and will try defragging it a couple more times and give it another whirl.

---

### Post by presence1960 on 2009-08-05
> **Balagast said:**
> I should clarify a bit.  I was trying to edit the partition using the Ubuntu live CD partition editor.

I did try to defrag it a couple times.  I am currently running a diskchk and will try defragging it a couple more times and give it another whirl.

That will work , same instructions for shrinking XP and creating new partitions. I believe you can't create NTFS partitions from the Live CD, just FAT32 & FAT 16 if you want a partition to be shared between the two OSs. other than that it will work that way.

---

### Post by Balagast on 2009-08-05
> **presence1960 said:**
> That will work , same instructions for shrinking XP and creating new partitions. I believe you can't create NTFS partitions from the Live CD, just FAT32 & FAT 16 if you want a partition to be shared between the two OSs. other than that it will work that way.

When I originally try to edit that partition though, it didn't even give me an option to resize it.

---

### Post by FCS tech on 2009-08-05
What would happen if you ignored all this.:oops: Like say maybe you installed xp then for fun you installed 9.04 also without partitioning. My laptop dual boots like this and everything seams to be runing ok. Am i looking at trouble down the road? This has only been a week.

---

### Post by presence1960 on 2009-08-05
Boot from the Ubuntu Live Cd and choose "Try Ubuntu without any changes...", when the desktop loads go Applications > Accessories > Terminal. Run this command from terminal ```
sudo fdisk -l
``` That is a lowercase L at the end. Post the output back here. We'll see what your partition table looks like.

---

