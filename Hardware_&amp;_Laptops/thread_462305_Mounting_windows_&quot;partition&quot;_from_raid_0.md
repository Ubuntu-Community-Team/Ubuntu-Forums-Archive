---
title: "Mounting windows &quot;partition&quot; from raid 0"
date: 2007-06-02
forum: Hardware &amp; Laptops
---

### Post by gth740k on 2007-06-02
I'm trying to mount my windows drive(s) so i can access my files from ubuntu.  I'm using the ntfs-3g driver and config tool.  For reference, I have windows on a 2disk raid0 array, and ubuntu on a separate 3rd drive.  I think the problem is that my windows 'drive' is really 2 drives in raid 0.  When i run fdisk -l it shows both individual disks, but not one that represents the raid.  So every time i try to mount sda1 (the partition that shows up on sda, the first drive in the raid0 array) i just get errors telling me stuff is courrupt.  

Is it possible to workaround this, or is my only option to make a "windows" partition on my ubuntu drive and copy over the files i want to use?

---

### Post by bone43 on 2007-06-02
> **gth740k said:**
> I'm trying to mount my windows drive(s) so i can access my files from ubuntu.  I'm using the ntfs-3g driver and config tool.  For reference, I have windows on a 2disk raid0 array, and ubuntu on a separate 3rd drive.  I think the problem is that my windows 'drive' is really 2 drives in raid 0.  When i run fdisk -l it shows both individual disks, but not one that represents the raid.  So every time i try to mount sda1 (the partition that shows up on sda, the first drive in the raid0 array) i just get errors telling me stuff is courrupt.  

Is it possible to workaround this, or is my only option to make a "windows" partition on my ubuntu drive and copy over the files i want to use?


Here where I would try..

[http://forum.ntfs-3g.org/index.php](http://forum.ntfs-3g.org/index.php)

 I have no idea other than to ask above Im a chicken and stayed away from my raid 0 box after reading a few posts about ntfs, windows, raid 0 and ubuntu.

 but good luck and please if you get it to work post back maybe then i might try it on my other rig!

---

### Post by gth740k on 2007-06-02
Thank you for the the link.  I'll let you know if I get anywhere.

---

### Post by gth740k on 2007-06-04
Success!  After a rejuvenating weekend, I decided to tackle this project.  Which, in the end, only took about 10 minutes of forum browsing and slight tweaking.

The forum thread that helped me is here: [http://forum.ntfs-3g.org/viewtopic.php?t=400](http://forum.ntfs-3g.org/viewtopic.php?t=400)

I was mounting a software raid0 (from my intel motherboard's controller) and needed the dmraid driver.  After installing that, I changed the device path to /dev/mapper/<my raid name> in the fstab.  sudo mount -a and I was browsing my raid in no time.

Of course everyones situation is different.  I encourage anyone needing help mounting ntfs partitions using ntfs-3g (raid or otherwise) to look at [http://forum.ntfs-3g.org/index.php](http://forum.ntfs-3g.org/index.php)

---

