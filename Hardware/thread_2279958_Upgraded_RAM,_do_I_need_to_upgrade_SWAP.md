---
title: "Upgraded RAM, do I need to upgrade SWAP?"
date: 2015-05-26
forum: Hardware
---

### Post by Dev'olution on 2015-05-26
Hi there,

I've just upgraded my RAM on my PC from 4GB to 16GB. 

At the time of install I had a 4.2GB swap, but am unsure if I need to up my SWAP size or not? And if so, how is the easiest/safest way to do so?

Cheers,

WAU

---

### Post by QIII on 2015-05-27
With 16GB of RAM, it is extremely unlikely that you will ever need swap in normal operations.  I don't even create a swap partition any more.

However, if you are going to hibernate your machine, you need at least the same amount of swap as you have RAM to save the entire RAM state.  I usually suggest about 1.1 x RAM just for some padding.

Do you hibernate the machine?

---

### Post by Dev'olution on 2015-05-27
On occasion I would, but not yet with my 16GB of RAM. 

How would I modify my SWAP drive without my main partition eating dust?

---

### Post by mastablasta on 2015-05-27
but do you need 16 gb SWAP even when you hibernate a desktop (no other apps loaded)? why would you need so much?

---

### Post by grahammechanical on 2015-05-27
Unless you have several gigabytes of unallocated disk space then the only way to increase the size of one partition is to reduce the size of another. We always get a warning when resizing partitions. It is right that we get that warning but I have never wrecked my Ubuntu installation by resizing it to get space for another partition.

Regards.

---

### Post by v3.xx on 2015-05-27
> **QIII said:**
> With 16GB of RAM, it is extremely unlikely that you will ever need swap in normal operations.  I don't even create a swap partition any more.

However, if you are going to hibernate your machine, you need at least the same amount of swap as you have RAM to save the entire RAM state.  I usually suggest about 1.1 x RAM just for some padding.

Do you hibernate the machine?
Nailed it :)

I run a 2G swap partition w/24G of ram, just saves a step when installing something new.  It rarely gets used, some processes will use swap as storage so from time to time I see a few Meg being used.

Swap can be enlarged using gparted and I have found this has a fare chance of failure.  A resize usually requires the beginning of the swap partition be moved, this (as with any partition) can be a problem.

You can also set swappiness.
[https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F](https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F)

---

### Post by weatherman2 on 2015-05-27
There is no point in resizing a swap partition - just erase it to create free space, then resize another partition to make room for a larger swap.  Then create a new swap.  (If you do it this way, be sure to update /etc/fstab to update the new swap partition's UUID - and if you hibernate, update the file/etc/initramfs-tools/conf.d/resume with the new UUID, then run "sudo update-initramfs" .)

It's true that moving the beginning of a partition can be very time consuming - but moving the end can be very quick, even a few seconds, depending on how much free space the partition has.  I usually put swap at the very end of my disk (if not using an LVM) so it can be resized as I describe.

And yes - it's always a good idea to make backups before attempting a resize.  Although I've resized many partitions successfully with Gparted without incident, you never know.

If you are trying to resize your main OS partition, you'll need to boot from a live USB to do it.

And if you think you'll ever need to worry about this stuff, you should look into using an LVM, which makes resizing partitions much easier, but you need to setup an LVM at install time.  I rarely do installs without LVM anymore - there are too many advantages (for example, snapshotting so you can make valid backups of a live partition).

---

