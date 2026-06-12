---
title: "Mounting Error"
date: 2005-11-16
forum: Hardware &amp; Laptops
---

### Post by souled on 2005-11-16
When I try to mount /dev/hdb5 which is a 75GB ext3 partition I get this error 
```
mount: wrong fs type, bad option, bad superblock on /dev/hdb5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

I try and mount it with this command (which I've done successfully before):
```
sudo mount -t ext3 /dev/hdb5 /media/storage
```
This partition is only a few days old with barely anything on it... I'm not sure why it stopped working.
Here is the output of dmesg | tail:
```
[4294740.892000] ibm_acpi: ec object not found
[4294761.044000] NET: Registered protocol family 10
[4294761.044000] Disabled Privacy Extensions on device c02eb280(lo)
[4294761.044000] IPv6 over IPv4 tunneling driver
[4294771.475000] eth0: no IPv6 routers present
[4296245.751000] hdb: task_in_intr: status=0x59 { DriveReady SeekComplete DataRequest Error }
[4296245.751000] hdb: task_in_intr: error=0x40 { UncorrectableError }, LBAsect=16128, high=0, low=16128, sector=16128
[4296245.751000] ide: failed opcode was: unknown
[4296245.751000] end_request: I/O error, dev hdb, sector 16128
[4296245.751000] EXT3-fs: Can't read superblock on 2nd try.

```

I have no idea what these errors mean. Can anyone help me out?

---

### Post by taurus on 2005-11-16
Are you sure /dev/hdb5 is ext3???  Since there is hardly anything on it, why not format it as ext3 and mount it again...

mke2fs -j /dev/hdb5

---

### Post by aysiu on 2005-11-16
What comes out for /dev/hdb5 when you type ```
sudo fdisk -l
```?

---

### Post by souled on 2005-11-16
Yes I'm positive it's ext3. Here's the output of sudo fdisk -l for my second hdd.

```

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               2        9563    76806765    f  W95 Ext'd (LBA)
/dev/hdb5               2        9563    76806733+  83  Linux

```

I used Partition Magic to create /dev/hdb5, and it created an extended partion for some reason... (which the ext3 partition is in)

---

### Post by souled on 2005-11-18
I reformatted my hdb and made a new ext3 partition. However, now I'm getting an error about the disk being read only. I have /dev/hdb1 mounted to /media/storage, and I did chown on the file,  but I still can't write to it. I already have stuff on it... but now I can't write anything to it. Whenever I try to edit something in /media/storage, it says I can't because it's on a read-only disk. Why is this happening?

---

### Post by aysiu on 2005-11-18
You don't chown partitions. You change the mount options in the /etc/fstab file. For more info on how /etc/fstab works, check this out:

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

To actually edit the file, type this in a terminal ```
sudo nano /etc/fstab
```

---

### Post by chusome on 2005-11-18
Sounds like you need to edit your /etc/fstab so that the partition gets mounted as rw to all users. I'm not sure but I think you might want it as follows:

/dev/hdb5       /media/hdb5           ext3    rw        0       2

---

### Post by souled on 2005-11-18
So then in the fstab what do I put to make my ext3 partition writable for my user (eric)? Putting the mount options as default it still doesn't allow me to write to it.

EDIT: When I do that, I still get the error that says it's on a read only disk. Even trying to do something on the partition as root I get the error about the read only disk.

---

### Post by taurus on 2005-11-18
Try to unmount it, then edit /etc/fstab, and add "umask=000" to the field  before the last two numbers.  Then run

sudo mount -a

If you are not sure where to add that, just send me your /etc/fstab or post it...

---

### Post by souled on 2005-11-18
I thought umask=000 only works on FAT partitions and not ext3.

---

### Post by souled on 2005-11-19
Help please! I don't want to sound annoying, but I really want to fix my problem. I've never had this happen to me before. Even when trying to do something on the partition with root I get an error saying it's a read-only filesystem! I'm going crazy!

Here is my fstab line for my partion ```
/dev/hdb1       /media/storage  ext3    rw      0       2
```

---

### Post by Gratarian on 2006-03-05
Since it is an ext3 partition you have to treat it as a standard linux drive. I used

/dev/hdb1   /mnt/DATA   ext3  rw,users,auto 0  2

then created directories on that partition and set the with

chown root:users <dir>
chmod 777 <dir>

This allows all users to write and read these directories.

---

