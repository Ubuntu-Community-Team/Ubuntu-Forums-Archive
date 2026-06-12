---
title: "mount: /dev/hdg1 already mounted or /mnt/ntfs250 busy"
date: 2005-06-14
forum: Hardware &amp; Laptops
---

### Post by tofudrifter on 2005-06-14
what am i doing wrong???

i use
sudo mount /dev/hdg1 /media/disk1 -t ntfs -o umask=0222
and it spits out
mount: /dev/hdg1 already mounted or /media/disk1 busy

but it isn't
sudo umount /dev/hdg1
umount: /dev/hdg1: not mounted

i've tries adding these to /etc/vstab
still no go

here is my fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9541    76638051   83  Linux
/dev/hda2            9542        9729     1510110    5  Extended
/dev/hda5            9542        9729     1510078+  82  Linux swap / Solaris

Disk /dev/hdg: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdg1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/hdh: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdh1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/hdi: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdi1   *           1       19457   156288321    7  HPFS/NTFS

Disk /dev/hdj: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdj1               1       24321   195358401    7  HPFS/NTFS

Disk /dev/hdk: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdk1               1       14593   117218241    7  HPFS/NTFS

Disk /dev/hdl: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdl1               1       14593   117218241    7  HPFS/NTFS

i'm using a 2.6.11 kernel with ac7 patch

edit here's my mount -l

/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
/dev on /.dev type unknown (rw,bind)
none on /dev type tmpfs (rw,size=5M,mode=0755)
usbfs on /proc/bus/usb type usbfs (rw)

---

