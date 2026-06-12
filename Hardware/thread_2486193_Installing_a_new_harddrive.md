---
title: "Installing a new harddrive"
date: 2023-04-22
forum: Hardware
---

### Post by claus on 2023-04-22
Hi,

I want to install a used 320 GB harddrive into my PC, but I'm unsure how to edit the fstab afterwards. The present fstab looks like this:
 
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=7951bfd5-b9bf-42cf-ab1d-f00ff68ccde4 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=61FD-5872  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
```

Especially what means UUID=7951bfd5-b9bf-42cf-ab1d-f00ff68ccde4?

TIA,

Claus

---

### Post by sudodus on 2023-04-22
It means that the identification, UUID, of the root partition is that string. You can find the UUIDs of the partitions on the drives via the command

```

sudo blkid -c /dev/null | grep -v loop
# and/or
lsblk -e7 -f

```

See ```
man fstab
``` for more details how to write a line for each partition on the new drive.

---

### Post by oldfred on 2023-04-22
You need to partition drive, suggest gpt over old (very old) MBR.
If ever installing to that drive, you may want an ESP and/or bios_grub partition as first partition(s). 
You can also use gparted but must change device label or default partitioning first.
With gparted select gpt under device, advanced over msdos(MBR) default partitioning before starting.

I like to label partitions.  You can use gparted, Disks, or command line
You then can mount by label which can have a bit more meaning the UUID. Choices:
by-id/  by-label/  by-partuuid/  by-path/  by-uuid/

sudo cp /etc/fstab /etc/fstab.backup
sudoedit /etc/fstab
# Anytime you edit fstab always do this before rebooting. If no errors it just remounts everything, but if errors you have to fix before rebooting or you may not be able to, Make sure you have partition unmounted if previously mounted when creating new mounts:
sudo systemctl daemon-reload
sudo mount -a

Bit older (example shows ext3, so old as ext4 standard) but fstab has not changed.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

[https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909](https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909)
[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198) &
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)

---

