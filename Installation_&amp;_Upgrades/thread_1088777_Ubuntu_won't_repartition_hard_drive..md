---
title: "Ubuntu won't repartition hard drive."
date: 2009-03-06
forum: Installation &amp; Upgrades
---

### Post by br4nd0n on 2009-03-06
I downloaded a live CD of Ubuntu 8.04 and decided to install it and make a dual boot of Vista and Ubuntu. When I got to the resize partition part it started to work but hung at 0% for over 30 mins. So I turned off the computer and decided to see if windows vista would still boot after I did that. It did but it had to do a disk check but now everything works fine. However, I tried to install Ubuntu again with resizing my partition and I was just going to let it set all night so it could repartition my hard drive. Because it was obviously working before I just didn't realize it. Anyways, so I started to resize the partition and it gave me and error message saying couldn't repartition drive. What can I do to fix this?

---

### Post by avtolle on 2009-03-06
Since you are using Vista, please use the Vista tool to resize that partition, so as to avoid potential corruption of your Vista installation. First, though, before beginning any resizing, defrag the HDD more than once. When shrinking the Vista partition, leave the room created as unallocated and the installer will take it from there.

---

### Post by br4nd0n on 2009-03-06
I tried repartitioning using disk management in Vista and it hung up for a minute and then said access is denied.

---

### Post by avtolle on 2009-03-06
Not too familiar with Vista, but do you need to be in administrator status to do this (or something like that, akin to becoming root in linux)?

---

### Post by br4nd0n on 2009-03-06
I am the administrator and have even turned off UAC. So there shouldn't be any reason its telling me access is denied.

---

### Post by Dallywood on 2009-03-06
I had the same problem at first with partitioning using the ubuntu install cd. I just had to play around with the size of the partitions until I got one that worked. Couldn't tell you why that worked for me though.

---

### Post by Mark Phelps on 2009-03-07
Accidental double -post. See next post for info ...

---

### Post by Mark Phelps on 2009-03-07
> **br4nd0n said:**
> I am the administrator and have even turned off UAC. So there shouldn't be any reason its telling me access is denied.

Unless you have unhidden the "real" Administrator account, your are NOT the Administrator; you are a general use with some admin rights.

However, that still should NOT prevent you from resizing the volumes.

For some tips on shrinking the Vista OS volume, see the link below:

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/")

Also, do NOT use the Ubuntu partitioner or GParted to shrink the Vista OS partition unless you have a Vista DVD lying around.  Sometimes, the Linux partitioners corrupt the Vista OS volume and leave it in a state where you have to boot from the Vista DVD and run Startup Repair to get Vista to boot again.

If you can't shrink the volume using Disk Manager, you would do better to get hold of a Windows-based partition manager such as Partition Magic, Paragon Disk Manager, Acronis Disk Director.

---

