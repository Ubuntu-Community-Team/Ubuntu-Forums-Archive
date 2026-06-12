---
title: "My External HDD won't mount"
date: 2008-12-24
forum: Hardware
---

### Post by EvilEnvi on 2008-12-24
I have a external Iomega TB HDD and it wont mount on ubuntu. everytime I try to go to it it says "cant mount volume" Unable to mount volume "iomega HDD".

---

### Post by taurus on 2008-12-24
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by EvilEnvi on 2008-12-24
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x17e817e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         551     4425876   83  Linux
/dev/sda2             552       24321   190932525    5  Extended
/dev/sda5           23945       24321     3028221   82  Linux swap / Solaris
/dev/sda6             552       23568   184883989+  83  Linux
/dev/sda7           23569       23944     3020188+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcbce2081

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    7  HPFS/NTFS

---

### Post by taurus on 2008-12-24
Try something like

```
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
df -h
```

---

### Post by EvilEnvi on 2008-12-24
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
$LogFile indicates unclean shutdown (0, 1)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/sdb1 ntfs-3g force 0 0

---

### Post by taurus on 2008-12-24
Well, looks like the last time you used that external drive, you just unplugged it instead of using the safely remove hardware option from windows to unmount it first.  Therefore, you can either reconnect it back to a windows machine and go through the safely remove hardware icon on the bottom right or use ntfsfix to fix it.

```
sudo apt-get update
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
df -h
```
Again, always unmount the drive first before you unplug it from a computer.

---

### Post by EvilEnvi on 2008-12-24
thank you so much happy holidays

---

