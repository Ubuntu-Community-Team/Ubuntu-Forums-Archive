---
title: "Ubuntu reinstall via cp?"
date: 2009-07-11
forum: Installation &amp; Upgrades
---

### Post by jprophet420 on 2009-07-11
When I set up my box I put 3 partitions on sda (80gb hdd for OS installs) and one partition on sdb (400gb media drive).

I have decided I want just kubuntu on my sda, and I cant repartition it with the information on it. I botched my MBR trying but reinstalled grub, so Im back up.

Is there any way I can zip the /, put it on the big drive, repartition the 80gb, and then put the install back on (the 80)?

---

### Post by coffeecat on 2009-07-11
It's not the most elegant solution (although it's probably the easiest in the circumstances), but you can use cp. A few caveats. Don't 'cp' from within a running installation; use the live CD. You need root permissions. You must be careful to choose the correct cp options (see below). The filesystem on sdb1 **must** be a Linux one; NTFS or FAT32 won't do. And once you've copied and copied back, you'll need to edit /etc/fstab and /boot/grub/menu.lst (again from the live CD) because if you've repartitioned, the partition UUIDs will have changed.

So...

Boot from the Live CD and mount the original root partition and the big sdb1 partition. Let's assume that your original root partition is mounted on /media/original and sdb1 on /media/sdb1. Open a terminal, and...


```
sudo cp -a /media/original/* /media/sdb1/
```... and go away and have a cup of tea. Repartition sda and use 'sudo cp -a' to copy back again. Now you have to edit fstab and menu.lst.

About cp options: you're lucky that -a fits the bill here. Check out man cp if you want the gory details. You'll see some threads saying you have to omit virtual directories such as /dev. Don't bother. I've done this several times and it works fine. Quick and dirty, but effective.

The other slightly more elegant solution is to use tar to tar/compress the whole of your root partition into one tar.gz or tar.bz2 file. I've used this method too - it's my preferred method of making installation backups.

---

### Post by jprophet420 on 2009-07-11
backup drive has to be linux filesystem eh? thanks for the info, I can pull it off but with a different drive. 5200 rpm, yuk.

---

### Post by coffeecat on 2009-07-11
> **jprophet420 said:**
> backup drive has to be linux filesystem eh?

Yes, because you have to retain ownership and permissions for each file/folder, and Windows filesystems don't support Unix/Linux permissions. The cp -a flag includes "--preserve=mode,ownership,timestamps".

---

