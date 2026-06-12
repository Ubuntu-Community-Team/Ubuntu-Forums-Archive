---
title: "[SOLVED] Seagate external USB hard drive not mounting"
date: 2008-06-02
forum: Hardware
---

### Post by YAOMTC on 2008-06-02
With Hardy, a Maxtor external drive needed no manual mounting, as it needed on Feisty. However, this Seagate one does not automatically mount, and I can't figure out what the command is. I've tried a previously listed "fix":
```
sudo mkdir /mnt/harddrive
sudo mount -t vfat /dev/sda1 /mnt/harddrive
```
but that didn't work:
```
mount: /dev/sda1 already mounted or /mnt/harddrive busy
mount: according to mtab, /dev/sda1 is mounted on /
```
Then I tried switching in sdb1 instead of sda1, but nothing happened there.

Unfortunately, my sister who I'm borrowing this from doesn't know the capacity, and it doesn't look like it has a model number or name on it.

---

### Post by zoiks on 2008-06-03
Monitor the file /var/log/messages to see what device it's showing up as, as well as look for potential problems automounting. For example, in an open window try "sudo tail -f /var/log/messages" and then plugging in your device.

---

### Post by YAOMTC on 2008-06-03
Result of 'sudo tail -f /var/log/messages':

```
Jun  3 17:22:57 YAOMTC-1 kernel: [17033.543594] usb 5-5: new high speed USB device using ehci_hcd and address 4
Jun  3 17:23:04 YAOMTC-1 kernel: [17040.755473] usb 5-5: configuration #1 chosen from 1 choice
Jun  3 17:23:04 YAOMTC-1 kernel: [17040.843104] usbcore: registered new interface driver libusual
Jun  3 17:23:04 YAOMTC-1 kernel: [17040.869092] Initializing USB Mass Storage driver...
Jun  3 17:23:04 YAOMTC-1 kernel: [17040.870181] scsi4 : SCSI emulation for USB Mass Storage devices
Jun  3 17:23:05 YAOMTC-1 kernel: [17040.871064] usbcore: registered new interface driver usb-storage
Jun  3 17:23:05 YAOMTC-1 kernel: [17040.871070] USB Mass Storage support registered.
Jun  3 17:23:10 YAOMTC-1 kernel: [17046.336215] scsi 4:0:0:0: Direct-Access     ST316002 3A               8.01 PQ: 0 ANSI: 0
Jun  3 17:23:10 YAOMTC-1 kernel: [17046.346951] sd 4:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
Jun  3 17:23:10 YAOMTC-1 kernel: [17046.348282] sd 4:0:0:0: [sdb] Write Protect is off
Jun  3 17:23:10 YAOMTC-1 kernel: [17046.350013] sd 4:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
Jun  3 17:23:10 YAOMTC-1 kernel: [17046.351263] sd 4:0:0:0: [sdb] Write Protect is off
Jun  3 17:23:10 YAOMTC-1 kernel: [17046.351276]  sdb: sdb1
Jun  3 17:23:10 YAOMTC-1 kernel: [17046.374003] sd 4:0:0:0: [sdb] Attached SCSI disk
Jun  3 17:23:10 YAOMTC-1 kernel: [17046.374076] sd 4:0:0:0: Attached scsi generic sg2 type 0
```
Then after powering off:
```
Jun  3 17:27:59 YAOMTC-1 kernel: [17334.496328] usb 5-5: USB disconnect, address 4
```

**EDIT:** Result of "sudo fdisk -l":
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009106b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18703   150231816   83  Linux
/dev/sda2           18704       19457     6056505    5  Extended
/dev/sda5           18704       19457     6056473+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2d4d776f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19455   156272256    c  W95 FAT32 (LBA)
```
So... It's FAT32. Is there anything I can do with that?

---

### Post by YAOMTC on 2008-06-04
.

---

### Post by zoiks on 2008-06-04
So after

```
sudo mount -t vfat /dev/sdb1 /mnt/harddrive

```

it still doesn't mount? (Assuming /mnt/harddrive exists)? Silly question - are you sure it's vfat and not ntfs?

---

### Post by YAOMTC on 2008-06-04
Well, no. I'm not sure what it is, exactly. It could be ntfs. But... it seems replacing "vfat" with "ntfs" doesn't work, and results in:
```
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
```
So... I'm doing something wrong here, but what?

---

### Post by YAOMTC on 2008-06-04
.

---

### Post by YAOMTC on 2008-06-06
.

---

### Post by YAOMTC on 2008-06-12
Still haven't gotten it to mount.

---

### Post by medic2000 on 2008-06-12
Post the output of "sudo fdisk -l" If it is ntfs and i think it is first install the ntfs-3g if not installed. Then mount it like: 
"ntfs-3g /dev/sdb1(or sdc1 whatever it is) /your_mountpointer. 
And visit [www.ntfs-3g.org](www.ntfs-3g.org)
Additionally read "man ntfs-3g"

---

### Post by YAOMTC on 2008-06-19
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009106b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18703   150231816   83  Linux
/dev/sda2           18704       19457     6056505    5  Extended
/dev/sda5           18704       19457     6056473+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2d4d776f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19455   156272256    c  W95 FAT32 (LBA)
```
So... It's FAT32. Is there anything I can do with that?

---

### Post by YAOMTC on 2008-06-23
.

---

### Post by slibuntu on 2008-06-23
Ok, its FAT32, and its detected under /dev/sdb1.

Make a mount point in /media by running ```
 sudo mkdir /media/sdb1
```

Now, to actually mount the drive, try the following 
```
sudo mount -t vfat /dev/sdb1 /media/sdb1
```

I cant think of any reason that would not work.

---

### Post by YAOMTC on 2008-06-23
Finally, it mounts! Thanks a lot!

---

### Post by gatorbrit on 2008-06-23
> **slibuntu said:**
> Ok, its FAT32, and its detected under /dev/sdb1.

Make a mount point in /media by running ```
 sudo mkdir /media/sdb1
```

Now, to actually mount the drive, try the following 
```
sudo mount -t vfat /dev/sdb1 /media/sdb1
```

I cant think of any reason that would not work.

Hi - I was having the same problem - and this mounts the seagate external hard disk fine.  But it only is read only.  How do I change permissions?

Thanks

Rich

---

### Post by slibuntu on 2008-06-23
There's a fix for that too, although I'm having the same problem and it didn't work for me, see [this]("http://ubuntuforums.org/showthread.php?t=835810&page=2") thread.
The workaround that seems to work for alot of people is to run this command ; 
```

sudo chown slibuntu:slibuntu -R /media/sdb1

```
Replacing slibuntu with your user name and if your mount point is different to the one above, replacing /media/sdb1 with your mount point.

---

