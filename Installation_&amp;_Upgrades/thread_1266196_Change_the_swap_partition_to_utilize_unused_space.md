---
title: "Change the swap partition to utilize unused space"
date: 2009-09-14
forum: Installation &amp; Upgrades
---

### Post by maximilion on 2009-09-14
Hi :)

When installing Xubuntu 8.10.4, I shrunk the previous linux partition to 16GB, hoping to free up 64GB for storage. I kept the 1GB swap partition.

GPartEd says I have the maximum of 4 primary partitions, and so I can't create a partition in the unused space.

I've conjectured a few possibilities, please let me know if it destroys my Xubuntu if I mess with the swap partition using the LiveCD !!

1) Can I turn the swap partition into an extended partition, so I can create a new partition in the unused space?

2) Can I resize the swap partition to 65GB and make it NTFS, and put files beside the swapfiles there? (I'm guessing it needs the current filesystem.)

3) Can I resize (increase by 64GB) the windows primary partition just before the 16GB Xubuntu partition and reinstall Xubuntu, with guaranteed no trashing of my existing windows files?


If you can, please suggest the best alternative or a best solution. Thanks :)

---

### Post by stlsaint on 2009-09-14
im thinking that option 2 would be a bad one as the linux filesystem is ext...not ntfs(its just able to read ntfs and share it if needed)

i dont recommend making swap size 64 gb so best bet is to look into option 1...do a lil more research tho just to make sure!!

---

### Post by drs305 on 2009-09-14
It would be best if you can give us a screenshot from Gparted.

Is the swap partition the last one (farthest right)? If so, you can easily delete it (unmount it first), then create an extended partition, then recreate a small swap partition within the extended partition and make as many other logical partitions as you wish.

You don't *have* to have a swap partition so you will be able to unmount it and redo your partitioning. If the swap partition isn't the last one, things will be a bit more complicated and you will probably have to work from the Live CD. A lot of what we recommend depends on the location of the current free space.

---

### Post by maximilion on 2009-09-14
Wow, quick responses guys! Thx.

Yeah, hm, had to install gnome-utils to be able to take a screenshot, maybe PrtSc will work after a reboot. Anyway, here it is -

[IMG]http://bayimg.com/IADHcAaCo[/IMG]

Yeah, I'll try unmounting the swapdisk, removing it completely, and make an extended partition but saving 4GB in case I ever need to create a swapdisk.

That's possible while Xubuntu & gparted is running, I take it? I'll try anyway.

Thanks for the advice :)

---

### Post by drs305 on 2009-09-14
Thanks for the screenshot. Actually, you already have an extended partition (sda2), which is going to make things take a bit longer because of it's location.

Here is my recommendation. You will need to do this from the LiveCD or another CD such as the GParted CD or SystemRescue CD. 

This assumes you have nothing in sda5 (ntfs).

1.  Backup your important data!!!
2.  Boot to the live CD and open Gparted (System Administration, Partition Editor).
3.  Make sure you don't have anything (data) in sda5.
4.  Unmount swap (highlight the swap partition, then Partition, Swapoff).
5.  Delete sda5
6.  Delete sda2 (extended partition).
7.  Delete sda4.
8.  Move sda3 (linux) left against sda1. This will take a while.
9.  Create an extended partition with all the free/unallocated space.
10. Create a swap partition.
11. You will now have a lot of unallocated space to the right.
Make as many logical partitions as you wish.

You will have to edit your fstab to put the new UUID for the swap partition. Also check that the Ubuntu partition UUID has not changed.
```

sudo blkid -c /dev/null  # note the new swap partititon UUID
sudo mkdir /mnt/temp
sudo mount /dev/sda3 /mnt/temp  # mount the ubuntu partition
gksudo gedit /mnt/temp/etc/fstab # open fstab for editing

```
Save the file.

---

### Post by maximilion on 2009-09-14
(Funny, I can't seem to see my own screenshot in FF 3.5 on Windows... nothing in the HOSTS file... show images is on in forum options...)

Anyway, sda5 has vital data on it, so I guess I'll just have to sacrifice the swap partition and make a primary good old fat32 partition. It'll be for file storage only, so.

BTW, When I removed the swap partition in gparted, the two entries "Xubuntu" and "Xubuntu (recovery mode)" in GRUB were duped (top 2 rows duplicated), so that the default entry became memtest :P I'll fix that manually if all else fails.


Thx for your helpful suggestion, couldn't be implemented unfortunately.


Hm - I noticed GRUB2 in your sig - if you want to give your input to a nice solution to this [thread ]("http://ubuntuforums.org/showthread.php?t=1264713")you're welcome :)

---

### Post by drs305 on 2009-09-14
> **maximilion said:**
> Anyway, sda5 has vital data on it, so I guess I'll just have to sacrifice the swap partition and make a primary good old fat32 partition. It'll be for file storage only, so.

If you need to keep sda5, you could move your linux partition to the right end of the drive, then expand the sda2 extended partition to the right. That would allow you to bypass the 4 partition limitation.

I'll take a look at the other post.

---

