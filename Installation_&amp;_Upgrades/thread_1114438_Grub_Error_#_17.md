---
title: "Grub Error # 17"
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by magic-chef on 2009-04-02
I think I really screwed up!!!

I updated the computer on Monday (30th).  When I rebooted the computer kept saying there was something wrong with the filesystem and dropping into the CLI.

I decided to do a file system check (e2fsck).  I know....but, it's too late.  After momentarily losing my senses LOL I decided to do this on a mounted volume.  My Bad!

Now all I get is the Grub error #17.

Can I save it from here or am I lost?

---

### Post by upchucky on 2009-04-02
don't panic, even if the Linux kernel does....)

everything should be there. boot using the Ubuntu live cd then download this

[http://sourceforge.net/project/platformdownload.php?group_id=250055](http://sourceforge.net/project/platformdownload.php?group_id=250055) 

then do this

```
sudo bash ~/Desktop/boot_info_script*.sh
```

post the results here and im positive that someone will have the exact instructions to get things right.

---

### Post by meierfra. on 2009-04-02
I don't think the boot info script will reveal much.  I suggest to boot from the live CD and run a file system check from  the LiveCD. Make sure to unmount your Ubuntu partition before hand.

---

### Post by magic-chef on 2009-04-03
I have tried to boot from the Live CD.  It freezes at the beige screen (blank).  Is there a linux basic boot disk that I can go into a CLI and address the problem that I created by running a file system check with the ubuntu partition mounted.

Could this be the problem with the live cd (if it needs to write information to a partition)?

---

### Post by meierfra. on 2009-04-03
> Could this be the problem with the live cd (if it needs to write information to a partition)?
The LiveCD will not write to any of the regular partitions, but it will try to use the swap partition. (which shouldn't be a problem since nothing  should be wrong with your swap partition).  Do you have any other LiveCD you could try? Or you could download one (System Rescue, Gparted,puppy linux,knoppix,,,,) Just about any live CD will have "e2fsck" installed.

---

### Post by leonardo_neo on 2009-04-03
Try to solve this problem with "super grub disk".

To download and burn super grub disk, follow this link......

> [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

To know how "super grub disk" works, follow this link.....

> [http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

Hope this helps :)

---

### Post by magic-chef on 2009-04-08
Ok, I've tried the easy fix with the Supergrub.  It did not work.  I think my problem relates to using the e2fsck while the partition was mounted.  According to the partition information from Supergrub the operating thinks it is an ext2fs system when it is actually a ext3fs.  How can I get the file system to report itself as ext3fs without messing things up too bad.  Got a lot of info at stake.

---

### Post by meierfra. on 2009-04-08
Super Grub always reports ext3 partitions as ext2fs.  So that's not your problem.
You have to find some way run a file system check  on your corrupted partition.

---

### Post by magic-chef on 2009-04-12
How can I do that?

---

### Post by meierfra. on 2009-04-12
Quote from post 5:

> **meierfra. said:**
>  Do you have any other LiveCD you could try? Or you could download one (System Rescue, Gparted,puppy linux,knoppix,,,,) Just about any live CD will have "e2fsck" installed.

---

