---
title: "Digital Camera Card Drive"
date: 2005-08-27
forum: Hardware &amp; Laptops
---

### Post by reuben on 2005-08-27
Hi, my computer came with one of those multi-card readers -- it says "Access" on the front, but I don't think that's the brand name. I don't see anything under /etc/mtab or /etc/fstab that appears to be it, when I put cards in to be read. Is there a technique to getting this mounted? I believe it is scsi, not sure. 

Here's lspci:
0000:00:00.0 Host bridge: nVidia Corporation: Unknown device 00e1 (rev a1)
0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 00e0 (rev a2)
0000:00:01.1 SMBus: nVidia Corporation: Unknown device 00e4 (rev a1)
0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1)
0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1)
0000:00:02.2 USB Controller: nVidia Corporation: Unknown device 00e8 (rev a2)
0000:00:05.0 Bridge: nVidia Corporation: Unknown device 00df (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation: Unknown device 00ea (rev a1)
0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 00e5 (rev a2)
0000:00:0a.0 IDE interface: nVidia Corporation: Unknown device 00e3 (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 00e2 (rev a2)
0000:00:0e.0 PCI bridge: nVidia Corporation: Unknown device 00ed (rev a2)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
0000:02:0a.0 Ethernet controller: 3Com Corporation 3cSOHO100-TX Hurricane (rev 30)

lsusb:
reuben@69-12-142-24:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 005: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda8       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       /big1           ext3    defaults        0       2
/dev/sda6       /big2           ext3    defaults        0       2
/dev/hdd7       /docs           reiserfs defaults        0       2
/dev/hdd6       /home           reiserfs defaults        0       2
/dev/hdd5       /spare          ext3    defaults        0       2
/dev/sda9       /tmp            ext3    defaults        0       2
/dev/hdd1       none            swap    sw              0       0
/dev/sda7       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdb        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom2   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb1        /media/sdb1    vfat    sync,user,noauto,umask=000    0 0

cat /etc/mtab
/dev/sda8 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /dev/shm tmpfs rw 0 0
/dev/sda5 /big1 ext3 rw 0 0
/dev/sda6 /big2 ext3 rw 0 0
/dev/hdd7 /docs reiserfs rw 0 0
/dev/hdd6 /home reiserfs rw 0 0
/dev/hdd5 /spare ext3 rw 0 0
/dev/sda9 /tmp ext3 rw 0 0
/dev /.dev unknown rw,bind 0 0
none /dev tmpfs rw,size=5M,mode=0755 0 0
usbfs /proc/bus/usb usbfs rw 0 0

---

