---
title: "Resizing root partition"
date: 2009-02-10
forum: Installation &amp; Upgrades
---

### Post by xexets on 2009-02-10
Hi! I apologize if this is not the correct category, I could not find a more suitable one!

Now I have Xubuntu installed on a secondary partition. As was foreseeable I love it and decided to get rid of the windows partition. Could not do it in Xubuntu, so I downloaded Gparted live, run it, formatted windows partition to unallocated space, applied, clicked on the existing linux partition to extend it to all the available space and I just could not do it. I can't extend it beyond its present size. I reckon it might have something to do with the fact that it is a secondary partition, but I can't change it into a primary one either...
Any hints? What can I do? I would like to avoid installing from scratch...
Any help would be much appreciated, thank you  very much!

---

### Post by unutbu on 2009-02-10
By secondary partition I assume you mean it is a logical partition inside of an extended partition. If so, then you need to resize the extended partition first, and then resize the logical partition which resides within it.

The extended partition is a container partition. Extended and primary partitions can have a label such as sda1, sda2, sda3, or sda4. Labels of the form sdaX where X > 4 indicate the partition is a logical partition. 

So using GParted, click on the text line which corresponds to the extended partition, resize it, click Apply, then click on the linux root partition (in a logical partition), resize it and click Apply.

For maximum safety, backup your data before resizing partitions.

If you run into any trouble or the above does not make sense, 
please open a terminal (Applications>Accessories>Terminal) post the output of 
```

sudo fdisk -l
```

---

### Post by xexets on 2009-02-10
That did the trick! thank you very much, I am now waiting for the data to move, but I'm sure it's going to be fine. Thanks a lot for your time.

---

### Post by xexets on 2009-02-10
Hi! It worked fine.... but now I can't boot. It outputs: GRUB ERROR 17.
I tryed to boot from livecd, tryed the command:
grub-install --recheck /dev/sda2
it outputs:
could not find device for /boot: not found or not a block device.
Any clues?

---

### Post by xexets on 2009-02-10
Sorry. Followed this: [http://ubuntuforums.org/showthread.php?t=504678](http://ubuntuforums.org/showthread.php?t=504678) using xubuntu live cd. Solved! (I'm posting this just for future reference if it may be of any help to anyone!)

---

