---
title: "Vista partition does not (auto)mount"
date: 2008-05-30
forum: Hardware
---

### Post by chubakabra on 2008-05-30
Hi

For some reason my Vista partition does not (auto)mount in my freshly installed xubuntu 8.04 on my HP Compaq 8710w laptop. It is nowhere to be found at all. This has not been an issue in in any other distros I've tried (Ubuntu, Kubuntu. Mint, Mepis, openSUSE....). I even think that it was not an issue with the live xubuntu cd either.

Starting Gparted gives an error message:

"Failed to mount "79G Volume"

org.freedesktop.hal.storage.mount-fixed auth_admin_keep_always <-- (action, result)."

I'm no Linux expert and have no idea what causes this or where to start digging. Any suggestions?

Best regards
Olav

---

### Post by ajmorris on 2008-05-31
hi there,
do the following from a terminal:
```
sudo apt-get install ntfs-3g
```
then post here the contents of /etc/fstab
and the output of sudo fdisk -l

AJ

---

### Post by chubakabra on 2008-06-01
Hi

The ntfs-3g package was already installed.

I have kind of fixed this myslef i think by adding a line to /etc/fstab (the last one):

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=5551b847-b70d-4b6d-8c32-0da3c3d0aebc /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=2371ed5a-fda8-4667-808b-566622d2f101 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

/dev/sda1 /media/Windows ntfs nls=utf8,umask=0222 0 0
```

It works, but i do not know why it didn't work before, why it wasn't automatically detected like on the other distros. It automounts to the media/Windows directory i created.

However - not that it matters a lot though - the partition does not show in the "Places" menu.

This is the fstab -l output, just for the record:

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe739759e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9697    77891121    7  HPFS/NTFS
/dev/sda2           13546       14593     8418028+   c  W95 FAT32 (LBA)
/dev/sda3            9698       13545    30909060    5  Extended
/dev/sda5            9698       13381    29591698+  83  Linux
/dev/sda6           13382       13545     1317298+  82  Linux swap / Solaris

Partition table entries are not in disk order
```

Hope everythong looks ok now? Or have I done anything unwise?

Best regards
Olav

---

### Post by ajmorris on 2008-06-03
yep, thats all fine, the only thing is, your fstab entry.
you have: /dev/sda1 /media/Windows ntfs nls=utf8,umask=0222 0 0

There is absolutely nothing wrong with this, however, i just thought id mention, that with that, you are using the Kernel ntfs driver, not the one installed from ntfs-3g, to use ntfs-3g instead, just replace ntfs with ntfs-3g, however, either drivers are fine :)

AJ

---

### Post by gibberz on 2008-06-09
Hi there chubakabra , just thought i`d add that to get a short cut to any folder in the places menu just open thunar(Xubuntu file manager) and drag what ever folder you want to be a short cut into the side bar. From then on you should see those short cuts show in the places menu.


hope that helps a bit cheers! :)

---

