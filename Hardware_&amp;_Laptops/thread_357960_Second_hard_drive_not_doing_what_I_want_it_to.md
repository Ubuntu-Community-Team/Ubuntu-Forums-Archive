---
title: "Second hard drive not doing what I want it to"
date: 2007-02-10
forum: Hardware &amp; Laptops
---

### Post by sarithelsd on 2007-02-10
Hi,
I'm running ubuntu 6.10, and I just installed a second hdd to be used exclusively with ubuntu.  i formatted the drive and when i run "sudo fdisk -l" both hdds are shown.  I mounted the hdd to /mnt/hd2/.

Now here's where I get sad.  I moved some media into the drive (which i had to do by sudo mv, I wish there was a better way to write to my secondary drive), but when I open the drive, it says that the free space equals the free space in my primary drive.  furthermore, moving 35 GB of stuff so far into my secondary drive has not increased the amount of free space in the primary drive.

The primary drive is 320.0 GB seagate, 60 GB NTFS running XP and the rest running Ubuntu; the ubuntu space has 100 GB free.  The secondary drive is a 500 GB maxtor.

In conclusion:
Why does the bottom of the window when I open /mnt/hd2/ display the Free Space: as 100 GB, rather than ~500 GB?  (When I mount my laptop to /mnt/laptop, it displays the Free Space: as the amount of free space on my laptop hard drive)  Why does moving files to /mnt/hd2/ not increase the free space on the primary drive?  And, is there a way to have my secondary drive as easily writeable as my primary drive (can I give myself permissions somehow to write to it?)?

---

