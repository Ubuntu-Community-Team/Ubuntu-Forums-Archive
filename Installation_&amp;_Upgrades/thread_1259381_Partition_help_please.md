---
title: "Partition help please"
date: 2009-09-06
forum: Installation &amp; Upgrades
---

### Post by bri3 on 2009-09-06
How are you guys doing, I've partition my pc and laptop before to use Ubuntu, but I really cant seem to wonder why I can't partition my NTFS file system that Win 7 is sitting on, on my new laptop.  I have a 11.7 unallocated partition, and the other partition is 200 and something gigs of the NTFS partition, I have a 320 gig HD.

First of all, is there anyway possible I can move the 11.7 unallocated partition to the NTFS partition and make it one partition? I've tried it and I can't seem to do it.  I'm using the ubuntu live disc partition wizard, I also pulled up the terminal and used gparted, and it will only let me use the unallocated partition to put ubuntu on, it is not letting me alter the NTFS file system, please guys some help would be appreciated.  

Summary:
Want to use the NTFS (which is about 240 gigs free) to put Ubuntu on.
As of right now, I'm only able to put Ubuntu on the unallocated 11.7 gig partition.
I want to join the 11.7 gig partition to the NTFS partition.

Thank you.

---

### Post by Sam Lars on 2009-09-07
You can delete the NTFS and then make a new, bigger partition, or you can resize the NTFS... but the unallocated has to be next to the partition you want to add it to. Could you give us some screenshots or something of what you're looking at?

---

### Post by hubertofliege on 2009-09-07
I'm helping a friend install Jaunty, but at the partition screen, the windows partition cannot be shrunk.  It does not even offer the opportunity to install both side-by-side.  Why can't I resize windows?  It has 16 GB of free space on the disk.

---

### Post by Cheezespread on 2009-09-07
> **hubertofliege said:**
> I'm helping a friend install Jaunty, but at the partition screen, the windows partition cannot be shrunk.  It does not even offer the opportunity to install both side-by-side.  Why can't I resize windows?  It has 16 GB of free space on the disk.

Please create a thread of your own when you ask a new question. Thanks !

Anyway, I assume that you are using Vista right now.Windows won't let you shrink the volume if you have some data at the end of the volume. 
1. Try [defragging ]("http://www.auslogics.com/disk-defrag/index.php")the drive . 
2.Disable systme restore for the time being

Please check if you are able to shrink it after this.


Please have a look in [here ]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/")as well which might serve your purpose.

---

### Post by Sam Lars on 2009-09-14
Thanks for the screenshots. Feel free to post them in the thread next time.
You want to choose the Resize/Move option for the NTFS partition. This will let you resize it to fill the drive.
I don't know if it will let you install Ubuntu on NTFS... it would erase everything on there. If you want to have both the NTFS and the Ubuntu, then you should install in the unallocated space.

---

