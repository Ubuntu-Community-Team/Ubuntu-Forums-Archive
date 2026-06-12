---
title: "Merging /boot with /"
date: 2009-07-08
forum: Installation &amp; Upgrades
---

### Post by Intrepid Ibex on 2009-07-08
I just have decided to merge my '/boot' with '/' because I don't want to have separate partitions of them both.

So how to do this?

**Easy way to get your post counter up and running.**

---

### Post by dstew on 2009-07-08
I don't know if there is an automatic way to do this, but here is how I would do it.

Create a new mount point, like /media/old_boot. Unmount the /boot partition from its /boot mount point, and mount the /boot partition  to the new mountpoint.```
sudo mkdir /media/old_boot
sudo umount /dev/sda1
sudo mount /dev/sda1 /media/old_boot
```This of course assumes your /boot parition is /dev/sda1.

Copy the contents of the /boot partition to the /boot directory in your root file system partition (the directory should already be there, because it served as the mount point for the /boot partition):```
sudo cp -r /media/old_boot/ /boot/
```

That should put all the files, including the kernel and the /boot/grub directory in there.

Next, you will need to re-install grub in order to boot. The old grub was installed to get its stage2 from the /boot partition. But before you do, you need to edit the menu.lst file so that the kernel lines will be correct. If you used a /boot partition, your kernel files will be named /vmlinuz-2.6.*****, but if you use the kernels in the /boot directory on the root file system, they need to be renamed **/boot**/vmlinuz-2.6.***** etc. Same for the initrd files. Also, the grub root will need to be changed, since it referred before to the /boot partition, and now it will be using the / partition. I think the roots for the kernel lines will be the same, since they refer to the root file system partition. You might also have to edit the /etc/fstab file, if there is a line in there which mounts the /boot partition. Just remove the line.

Once you edit the menu.lst file, you can shut down, boot a live CD and [re-install grub]("http://ubuntuforums.org/showthread.php?t=224351as:"), with the root now referring to the root file system. I think the grub command **find /boot/grub/stage1** will return the proper root, as long as you have copied the contents of the /boot partition into the /boot directory. If it boots after you re-install grub, and you are sure it is using the /boot directory, rather than the /boot partition, you can delete the /boot partition, and expand the / partition to take over the unallocated space.

You can probably guess that if this is wrong (I have not tried it personally) or if you make a mistake, you will end up with an un-bootable system. It is probably wise to look at other posts, and google around a bit before acting.

---

### Post by Intrepid Ibex on 2009-07-24
Well you can revert the changes any time. But yeah, I did a little different (same idea) and that worked -b... so:
```
# first copied the contents of boot to a temporary dir
mkdir /tmp/boot
cp /boot /tmp/boot -r

# umounted the boot partition
umount /boot

# moved the contents back into the boot directory
mv /tmp/boot/* /boot/

# and finally removed the line from fstab that mounts the boot partition
```I then reconfigured menu.lst.:

Old menu.lst:
```
title  Arch Linux
rootnoverify   (hd0,**0**)
kernel /vmlinuz26 root=/dev/disk/by-uuid/e289f40b-c778-4583-8bae-1f0bd769b311 ro
initrd /kernel26.img

title  Arch Linux Fallback
rootnoverify   (hd0,**0**)
kernel /vmlinuz26 root=/dev/disk/by-uuid/e289f40b-c778-4583-8bae-1f0bd769b311 ro
initrd /kernel26-fallback.img
```New menu.lst:
```
title  Arch Linux
rootnoverify   (hd0,**2**)
kernel **/boot/**vmlinuz26 root=/dev/disk/by-uuid/e289f40b-c778-4583-8bae-1f0bd769b311 ro
initrd **/boot/**kernel26.img

title  Arch Linux Fallback
rootnoverify   (hd0,**2**)
kernel **/boot**/vmlinuz26 root=/dev/disk/by-uuid/e289f40b-c778-4583-8bae-1f0bd769b311 ro
initrd **/boot**/kernel26-fallback.img
```

---

