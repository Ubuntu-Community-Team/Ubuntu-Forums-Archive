---
title: "USB stick on EeePC not mounted after install"
date: 2008-05-20
forum: Hardware
---

### Post by amsdiesel on 2008-05-20
hi all

right after installing gutsy gibbon on a eeepc, after restart I'm no longer able to mount my ub stick

that's what I got:
manuel@gypsy:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults       0       0
# /dev/sdb1
UUID=ada5ddaf-5886-48fb-a567-887eb1163e36 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=95d37faf-c4b4-411e-b53d-aadb045c4fd2 none            swap    sw              0       0
/dev/sdd1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

If I try to open it says it cannot be mounted, and mounting it by terminal fails.

If I reboot and try to boot from USB I'm able to do that, but reinstalling didn't sorted any effect.

I read that reinstalling HAL could solve this sometime, but it has a bunch of dependencies, including xubuntu-desktop and network, so I won't be able to reinstall em.


that's what fdisk reports

manuel@gypsy:~$ sudo fdisk -l
[sudo] password for manuel:

Disk /dev/sda: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2c512c51

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         300     2409718+  83  Linux
/dev/sda2             301         488     1510110   83  Linux
/dev/sda3             489         489        8032+   c  W95 FAT32 (LBA)
/dev/sda4             490         490        8032+  ef  EFI (FAT-12/16/32)

Disk /dev/sdb: 16.1 GB, 16139354112 bytes
255 heads, 63 sectors/track, 1962 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003b43a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1894    15213523+  83  Linux
/dev/sdb2            1895        1962      546210    5  Extended
/dev/sdb5            1895        1962      546178+  82  Linux swap / Solaris

Disk /dev/sdd: 1010 MB, 1010826752 bytes
255 heads, 63 sectors/track, 122 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         123      987104    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(121, 254, 63) logical=(122, 227, 40)



tnx in advance

---

### Post by amsdiesel on 2008-05-20
sorry, now working fine

can anybody delete this message? i don't find how to...

i just opened thunar with sudo thunar, and then tried to mount volume and it worked.
I still don't understand why in terminal and as root didn't worked...

maybe the solution is here, I think HAL wasn't mounting it...but I'm kinda new to linux...

manuel@gypsy:~$ sudo thunar
Thunar: Failed to connect to the D-BUS session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
thunar-volman: No property info.capabilities on device with id /org/freedesktop/Hal/devices/usb_device_1307_163_071028e0d9e0c1.
thunar-volman: No property info.capabilities on device with id /org/freedesktop/Hal/devices/usb_device_1307_163_071028e0d9e0c1_if0.
thunar-volman: No property info.capabilities on device with id /org/freedesktop/Hal/devices/usb_device_1307_163_071028e0d9e0c1_if0_scsi_host_scsi_device_lun0.
gnome-mount 0.6

---

### Post by Bubba64 on 2008-05-20
I don't think they moderators delete, especially when you gave an answer to your problem mark it as solved by logging in and mark as solved. I could be wrong about the delete.

---

