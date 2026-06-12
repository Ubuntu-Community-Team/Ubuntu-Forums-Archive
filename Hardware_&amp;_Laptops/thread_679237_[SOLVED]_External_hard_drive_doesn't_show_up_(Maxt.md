---
title: "[SOLVED] External hard drive doesn't show up (Maxtor DiamondMax 21)"
date: 2008-01-26
forum: Hardware &amp; Laptops
---

### Post by YAOMTC on 2008-01-26
I tried installing WoW from the discs, but that doesn't work; apparently I need to transfer files from a computer that has it installed already. So the guy that owns it put the folder on a Maxtor DiamondMax 21 USB external hard drive, but Ubuntu isn't recognizing it; it won't show up on the Desktop. I know that other people have had this problem, but I can't format it or anything, since it's not mine and he has other stuff on it.

Power Manager comes up when I plug it in and turn it on, but it says "Unable to get data..." in the tooltip.

I have ntfs-config and ntfs-3g installed.

I looked at several similar threads, and I tried [this]("http://ubuntuforums.org/showpost.php?p=3174762&postcount=14"), but it didn't do anything.

---

### Post by taurus on 2008-01-26
Can you post the outputs of these commands from a terminal, with the external drive plugged in and turned on?

```
dmesg | tail
sudo fdisk -l
df -h
```

---

### Post by YAOMTC on 2008-01-26
```
[  160.273579] sd 4:0:0:0: [sdb] Write Protect is off
[  160.273583] sd 4:0:0:0: [sdb] Mode Sense: 00 38 00 00
[  160.273587] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  160.274330] sd 4:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[  160.275076] sd 4:0:0:0: [sdb] Write Protect is off
[  160.275081] sd 4:0:0:0: [sdb] Mode Sense: 00 38 00 00
[  160.275083] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  160.275087]  sdb: sdb1
[  160.292748] sd 4:0:0:0: [sdb] Attached SCSI disk
[  160.292797] sd 4:0:0:0: Attached scsi generic sg2 type 0
```
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009106b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18703   150231816   83  Linux
/dev/sda2           18704       19457     6056505    5  Extended
/dev/sda5           18704       19457     6056473+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4f304f2f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS
```
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             142G   51G   84G  38% /
varrun               1010M  232K 1010M   1% /var/run
varlock              1010M     0 1010M   0% /var/lock
udev                 1010M  104K 1010M   1% /dev
devshm               1010M     0 1010M   0% /dev/shm
lrm                  1010M   34M  976M   4% /lib/modules/2.6.22-14-generic/volatile
```

---

### Post by taurus on 2008-01-26
Run

```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
ls -la /media/sdb1
```

---

### Post by YAOMTC on 2008-01-26
Upon running
```
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
```
I get
```
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/sdb1 ntfs-3g defaults,force 0 0
```
What should I do here? Should the drive be turned off?

---

### Post by taurus on 2008-01-26
It just means you didn't remove/unplug that drive cleanly the last time you used it.  Therefore, you need to include the force option to mount it.

```
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force
ls -la /media/sdb1
```

---

### Post by YAOMTC on 2008-01-26
That did it, thanks a lot!

---

### Post by YAOMTC on 2008-01-26
Wait... How do I unmount it, now?

EDIT: Never mind! I had typed "unmount" instead of "umount". Whoops.

---

