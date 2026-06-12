---
title: "Can't boot after RAID5 Reconfiguration"
date: 2005-09-15
forum: Hardware &amp; Laptops
---

### Post by spockboy on 2005-09-15
Hi there.

I set up Ubuntu 5.04 with a server install yesterday, and I'm loving it! :) (Well, I *was*)

I had 3x80GB IDE drives to install to, so I configured LVM on top of RAID5 array during the install. It went well, and everything was fine! Things went wrong when I installed some extra IDE drives, and shifted around the current drives onto different IDE buses and channels.

To give you a bit of insight into the boot process:
```

root  (hd0,0)
 Filesystem type is ext2fs, partition type 0x83
kernel  /vmlinuz-2.6.10-5-386 root=/dev/mapper/main-system ro quiet splash
   [Linux-bzImage, setup-0x1600, size=0x1209f6]
initrd  /initrd.img-2.6.10-5-386
   [Linux-initrd @ 0x1eb73000, 0x46d000 bytes]
savedefault
boot
Uncompressing Linux... Ok, booting the kernel.
audit(1126840987.754:0): initialized

Starting Ubuntu...
mdadm: no RAID superblock on /dev/hdc1
mdadm: /dev/hdc1 has wrong uuid.
mdadm: no RAID superblock on /dec/hdh1
mdadm: /dev/hdh1 has wrong uuid.
mdadm: no devices found for /devfs/md/0
  Found duplicate PV <PV-ID>: using /dev/ide/host2/bus1/target1/lun0/part1 not /dec/ide/host0/bus1/target0/lun0/part1
  Incorrect metadata area header checksum
  Incorrect metadata area header checksum
  Unable to find volume group "main"
pivot_root: No such file or directory
/sbin/init: 428: cannot open dev/console: No such file
Kernel panic - not syncing: Attempted to kill init!

```

I had configured a logical volume consisting of only one physical block device (the RAID array [FONT=Courier New]/dev/md0[/FONT]).

I initially had hoped that Ubuntu would detect the RAID superblocks on boot and see that the devices had merely changed bus locations, but as I found out later, it does not work like this. :-|

After a lot of Googling and absorbing information, I booted Ubuntu Live and attempting to modify the initrd image to change references of the old device locations to the new ones. But that didn't really work cause I wasn't sure what exactly I needed to change.

I'm hoping theres a simple way to recreate an initrd image that I can use to boot happily again.

I tried this:

```

root@ubuntu:/ #  sudo -i
root@ubuntu:/ #  mkdir /mnt/sysimage

## Scanned and activated my LVM volume containing the root of my system

root@ubuntu:/ #  vgscan
  Reading all physical volumes.  This may take a while...
  Found volume group "main" using metadata type lvm2
root@ubuntu:/ #  vgchange -a y main
  1 logical volume(s) in volume group "main" now active

## Mounted and chrooted to it

root@ubuntu:/ #  mount /dev/main/system /mnt/sysimage
root@ubuntu:/ #  chroot /mnt/sysimage

## Mounted the boot partition, which is on a separate device

root@ubuntu:/ #  mount /dev/hde1 /boot

## After some searching, I thought I might try this:

root@ubuntu:/ #  mount -t proc none /proc
root@ubuntu:/ #  dpkg-reconfigure linux-image-2.6.10-5-386
/usr/sbin/mkinitrd: device /dec/mapper/main-system is not a block device
Failed to create initrd image.

```
But that didn't work. I have no idea about initrd images!

Somebody help? :-|

---

### Post by tonym on 2005-09-16
I think the problem here is that you haven't got the /dev/mapper/main-system entry in your chroot'ed system.  You could try to copy this entry across before you chroot - might or might not work.

---

