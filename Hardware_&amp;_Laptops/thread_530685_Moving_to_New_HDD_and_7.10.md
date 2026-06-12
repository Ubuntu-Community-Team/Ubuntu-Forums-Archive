---
title: "Moving to New HDD and 7.10"
date: 2007-08-20
forum: Hardware &amp; Laptops
---

### Post by Dyus36 on 2007-08-20
tomorrow im getting a new harddrive, i plan to use it for storage as the 250gb i have now is all but full, so i decided while im at it i might as well try out the beta for 7.10, so my question is what would be the best way to backup all my stuff and move it back to the new os, im going to wipe Fiesty off instead of upgrading as i heard that causes less problems. any suggestions?

---

### Post by oddball on 2007-08-21
If your original disk is going to remain as the disk you boot from I would add the new disk, partition it, create an ext3 filesystem on it, mount it up somewhere then do somthing like:

cp -av /path/to/your/old/stuff/* /path/to/your/old/stuff

So lets assume it is your /home area you want to keep, and the new area is mounted to /mnt

```
cp -av /home/* /mnt /
```

Then when installing 7.10, during installation, make sure it doesn't format the new partition and tell it to mount it up at /home (if you want to be super safe during install you could unplug the new drive and configure the mounts up after)

I always make sure my /home area is on a separate partition so that when changing distros I can leave it sat there quite happily while I blow away the / and swap partitions.

---

