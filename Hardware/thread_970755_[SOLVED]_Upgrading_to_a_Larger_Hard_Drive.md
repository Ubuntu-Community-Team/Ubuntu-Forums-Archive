---
title: "[SOLVED] Upgrading to a Larger Hard Drive"
date: 2008-11-04
forum: Hardware
---

### Post by tommygunner on 2008-11-04
I have a 40GB hard drive that is running out of space. I've decided to upgrade to a 80GB drive. I'm wondering what the best way of doing this.

What I would like to do is copy the contents to the new 80GB drive. What is the best way to do this?

I was thinking I probably need to run a CD program and copy the drive. Will something like System Rescue CD do this?

---

### Post by nixscripter on 2008-11-04
If your drive is partitioned in the traditional Ubuntu way:

```

hda1   /boot
hda2   swap
hda3   /

```

My advice is to just copy the disk, byte for byte, from one to the other, update the partition table to fill the new space, and expand the root filesystem to fill up the disk.

If the old drive is **hda** and the new drive is **hdb** then you can boot off of an Ubuntu LiveCD and do this:

```
dd if=/dev/hda of=/dev/hdb
resize2fs /dev/hdb3
fdisk /dev/hdb **# delete partition 3, recreate it with all remaining disk space**

```

By the way, whatever you do, make sure you back up your data before trying anything. Playing with disk partitions is always dangerous.

---

### Post by tommygunner on 2008-11-05
cool, thanks. I'll try your suggestion.

---

