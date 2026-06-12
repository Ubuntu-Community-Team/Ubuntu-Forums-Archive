---
title: "No DVD-RW drive on VIA Mini-ITX board"
date: 2008-06-20
forum: Hardware
---

### Post by AChapin on 2008-06-20
Hello,

I'm not new to linux, but not very well versed in linux hardware management. I have a self-built box that is based on a VIA MN-800 motherboard. I cannot see or access my DVD-RW drive. This is the drive that I used to install the system, and can be seen via bios. Here are the outputs of some of the tests I have run.


fstab
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=516477e5-d603-4130-aa1f-2dd4730c5d39 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=1e42e827-bf0b-4f25-b138-b874546d88db none            swap    sw              0       0
**/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0**

Something was seen, but from the other results, it looks like it cannot be found.

mtab
> 
/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-19-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
gvfs-fuse-daemon /home/mw/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=me 0 0


lspci
> 00:00.0 Host bridge: VIA Technologies, Inc. VT8623 [Apollo CLE266]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:0d.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8623 [Apollo CLE266] integrated CastleRock graphics (rev 03)


and finally, lshw -C disk (which I found was suggested by someone else when I was looking into the problem)
>   *-disk                  
       description: ATA Disk
       product: TOSHIBA MK1233GA
       vendor: Toshiba
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: AA01
       serial: 85340121A
       size: 111GiB (120GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0000de18


thanks in advance!

---

### Post by pietjanjaap on 2008-06-22
disconnect the drive.
start ubuntu, remove entries in fstab.
reboot and check fstab.
shutdown. connect drive.
reboot?

---

### Post by AChapin on 2008-06-23
Tried it, and no dice. The only thing that changed is that the cdrom line is gone from fstab. Thanks for the suggestion, though!

---

