---
title: "How to load grub and mbr onto a partition ?"
date: 2009-07-16
forum: Installation &amp; Upgrades
---

### Post by rocdoc on 2009-07-16
I have ghosted a partition of a remastered Xubuntu distro onto an external drive using "dd". The drive device name is /dev/sda3. This external drive will be used as a master drive to ghost onto a number of other machines to make installing the modified Xubuntu onto a number of machines quicker. So I need to install Grub to /dev/sda3 so that I do not have to load Grub on every ghosted machine. Thus I want the bootloader on /dev/sda3, not /dev/sda.

I am unsure how to get grub and its MBR properly installed properly onto /dev/sda3. Any ideas appreciated.

Larry

---

### Post by dstew on 2009-07-16
> I am unsure how to get grub and its MBR properly installed properly onto /dev/sda3.One point to clear up, the MBR is the "Master Boot Record", which does not belong to grub, nor to any partition. It is the first sector on the disk, and contains the disk partition table, and maybe a boot loader if you want one there.

I am not sure exactly what you want to do. The dd command does a sector-by-sector copy. If you want to copy a whole disk, including the MBR, you can do it by```
dd if=/dev/sda of=/dev/sdc
```or whatever the output disk device name is. If the MBR had a grub boot loader in it, the new disk is potentially bootable.

If you want to copy a partition, the command is```
dd if=/dev/sda3 of=/dev/sdc3
```or whatever the output partition name is.

If you want to install grub to the MBR of a disk, you use the [usual commands]("http://ubuntuforums.org/showthread.php?t=224351"). If you want to install the grub boot loader to the boot sector of a partition, intending to chainload grub, you use the usual commands, except you do setup (hd0**,2**) instead of setup (hd0), for /dev/sda3.

Once you install grub into the MBR or partition boot sector, then if you copy the disk, or the partition, they will remain bootable. The one problem you may have though, is that the /boot/grub/menu.lst may refer to partitions by UUID. In that case, you might need to correct the menu with the correct UUID of the new partition(s).

---

### Post by raymondh on 2009-07-16
See Herman's GRUB page for tips.  'bout halfway down, if I understood your question.  If not, that site is still a heck of a reference.

[http://members.iinet.net.au/~herman546/p15.html#13](http://members.iinet.net.au/~herman546/p15.html#13)

Good luck.

---

