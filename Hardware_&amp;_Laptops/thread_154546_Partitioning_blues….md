---
title: "Partitioning blues…"
date: 2006-04-03
forum: Hardware &amp; Laptops
---

### Post by ssalman on 2006-04-03
I have a diskless/CDless laptop that can only boot through the hard drive and the network (through PXE)&#8230; I needed to resize one of my Resierfs partitions, and because I can&#8217;t use one of my installed Distros or liveCDs, I booted the Suse network install, and used it&#8217;s partitioner, but it looks like the partitioner only resized the partition and not the file system living within it. In short: I managed to screw up my partitions! I got fsck errors while booting my distros.

   
  After much fixing with fsck and resierfsck, I now can boot all my Distros with no problems. But there is still something wrong with my partition table or super block. Here is why:
   
  Qtparted starts with this error: Critical error during ped_disk_new! And then can&#8217;t find my partitions.
  Gparted: identifies my harddrive as unallocated space&#8230; the whole thing, there is not a single partition on there.
  Fdisk /dev/had and then the v command shows 308 unallocated sectors
   
  Still, I can boot with no error messages what so ever. And &#8220;fdisk &#8211;l&#8221; lists all my partitions and looks all correct.



how can I fix this mess, and is there a tool that can fix partition tables/super blocks/ HD devices?



Thanks for your help!!

---

### Post by vyruss on 2006-04-03
[QUOTE=ssalman]I have a diskless/CDless laptop that can only boot through the hard drive and the network (through PXE)&#8230; I needed to resize one of my Resierfs partitions, and because I can&#8217;t use one of my installed Distros or liveCDs, I booted the Suse network install, and used it&#8217;s partitioner, but it looks like the partitioner only resized the partition and not the file system living within it. In short: I managed to screw up my partitions! I got fsck errors while booting my distros.
   
  After much fixing with fsck and resierfsck, I now can boot all my Distros with no problems. But there is still something wrong with my partition table or super block. Here is why:
   
  Qtparted starts with this error: Critical error during ped_disk_new! And then can&#8217;t find my partitions.
  Gparted: identifies my harddrive as unallocated space&#8230; the whole thing, there is not a single partition on there.
  Fdisk /dev/had and then the v command shows 308 unallocated sectors
   
  Still, I can boot with no error messages what so ever. And &#8220;fdisk &#8211;l&#8221; lists all my partitions and looks all correct. how can I fix this mess, and is there a tool that can fix partition tables/super blocks/ HD devices?[/QUOTE]

Don't panic! :D

You can use **[gpart]("http://www.stud.uni-hannover.de/user/76201/gpart/")** to get your partitions back the way they were. Download the static binary version and put it on a floppy (or a CD, if you have a second CDROM). Then boot your PC from a live CD, and run gpart. This **g**uesses where your **part**itions should be on the disk. You then write down the information it gives you, paying extra special attention to the block numbers where each partition begins/ends. You then run fdisk and create partitions with exactly these settings, and you should get your system back. I know I have done it with good old gpart ;)

You can find more [detailed instructions **here**]("http://www.faqs.org/docs/Linux-HOWTO/LILO-crash-rescue-HOWTO.html#disk_partition_rescue").

Good luck!
Jimmy

---

### Post by vyruss on 2006-04-03
Hmm, I should have paid closer attention to your post, regarding your PC. If you cannot use gpart from the distro you are booting, you can try external CD drives or floppies, or usb sticks.

---

### Post by ssalman on 2006-04-03
Thanks Jimmy, I found the problem, I had a partition that starts and end with the same block number. deleted the partition, and all works fine now.

BTW - gpart was not able to figure out my partition table although it was good (other than the one bad partition).


Thanks! :)

---

### Post by vyruss on 2006-04-04
[QUOTE=ssalman]Thanks Jimmy, I found the problem, I had a partition that starts and end with the same block number. deleted the partition, and all works fine now.

BTW - gpart was not able to figure out my partition table although it was good (other than the one bad partition).[/QUOTE]

No prob, glad you found what was wrong. It's just that gpart is such a useful tool that I tell everyone about it, because one never knows when it's going to be needed ;)

Take care
Jimmy

---

