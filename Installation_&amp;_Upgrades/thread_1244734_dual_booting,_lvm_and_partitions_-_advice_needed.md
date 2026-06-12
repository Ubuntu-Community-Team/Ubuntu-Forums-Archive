---
title: "dual booting, lvm and partitions - advice needed"
date: 2009-08-19
forum: Installation &amp; Upgrades
---

### Post by ravenn on 2009-08-19
Hi,

I have a 230GB harddisk on which I have installed Windows XP and then added Ubuntu 9.04 with GRUB. I also managed to get LVM setup for the first time after reading through many articles and especially [http://distrowatch.com/weekly.php?issue=20090316](http://distrowatch.com/weekly.php?issue=20090316)

The problem I have is that Windows considers LVM as a logical drive occupying an extended partition and allows me to create only one primary partition using the entire free space available (I understand we can have only 3 primary and 1 extended partitions).
[IMG]http://i41.photobucket.com/albums/e298/GrateOne/partitions_in_windows.jpg[/IMG]

I thought of having the following structure and extending the volume group when necessary.
1. Primary partition - C: (Windows, Programs)
2. Extended partition,
    a. Logical drive - D: (Data)
    b. Logical drive - E: (Backups)

4. Primary partition - /boot
5. Logical storage (LVM)
    /home, /usr, /var, /tmp, swap etc. with free space.

Would it be possible to have this structure and add free space to LVM when necessary? It would be helpful if anyone could advise on this and let me know your thoughts O:)

Thanks,
Raven

---

### Post by lemming465 on 2009-08-20
I get better results in multiboot setups when I have all of the primary partitions in front of the extended partition, with the extended partition using up all of the rest of the disk, even if the logical partitions don't allocate all of the extended partition initially.  /boot can be a logical partition; Linux and Grub won't mind.  Unless you are planning to perhaps make an additional NTFS partition, I'd just allocate all the leftover space to the LVM partition.  Note that in your setup that is the only thing you could do with the extra space anyway; in your layout the extended partition doesn't include the extra space at the end of the disk and all the primary slots are used, so windows would have no options to get at it anyway.

While you can use *pvresize* to increase the size of an LVM partition after the fact, why create unnecessary future work for yourself?

---

### Post by ravenn on 2009-08-28
Thanks a lot for the advice lemming. I followed your suggestions and got the partition almost exactly like how I wanted it to be :) I was under the impression that /boot had to be on a primary partition. Now I have three primary partitions under Windows and /boot and all other volumes as logical from where I can comfortably access the Windows drives as well. Thanks again :)

---

