---
title: "Connecting a second external (USB) harddisk"
date: 2009-03-18
forum: Hardware
---

### Post by Bule on 2009-03-18
I've installed Ubuntu 8.10 on an external usb harddisk. It boots and runs from that disk.

Now i would like to access a second external usb harddisk. So far i haven't been able to do that and i could use some help. 

"fdisk -l" only shows the internal harddisk of the laptop and the external harddisk that it just booted from.

```

Disk /dev/sda: 100.0 GB, 100030242816 bytes
240 heads, 63 sectors/track, 12921 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x98f098f0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4116    31116928+   7  HPFS/NTFS
/dev/sda2            4117       12921    66565800    f  W95 Ext'd (LBA)
/dev/sda5            4117        7502    25598128+   7  HPFS/NTFS
/dev/sda6            7503       12921    40967608+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002aaeb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       11550    92775343+  83  Linux
/dev/sdb2           11551       12306     6072570    5  Extended
/dev/sdb3           12307       38913   213720727+   7  HPFS/NTFS
/dev/sdb5           11551       12306     6072507   82  Linux swap / Solaris

```

I'm a rookie when it comes to Linux.

---

### Post by Bule on 2009-03-18
Ok i have to change the question a bit.

I just thought to try booting with the extra external harddisk already connected. Now it does see and mount it.

So the question actual has to be how to connect and access a second external harddisk without having to reboot.

```

Disk /dev/sda: 100.0 GB, 100030242816 bytes
240 heads, 63 sectors/track, 12921 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x98f098f0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4116    31116928+   7  HPFS/NTFS
/dev/sda2            4117       12921    66565800    f  W95 Ext'd (LBA)
/dev/sda5            4117        7502    25598128+   7  HPFS/NTFS
/dev/sda6            7503       12921    40967608+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002aaeb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       11550    92775343+  83  Linux
/dev/sdb2           11551       12306     6072570    5  Extended
/dev/sdb3           12307       38913   213720727+   7  HPFS/NTFS
/dev/sdb5           11551       12306     6072507   82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x56cff240

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    c  W95 FAT32 (LBA)

```

---

### Post by taurus on 2009-03-18
```
sudo mkdir /media/sdc1
sudo mount -t vfat /dev/sdc1 /media/sdc1 -o umask=000
df -h
```

---

### Post by Bule on 2009-03-18
That didn't work.

I did "mkdir /media/USB". But when i try to mount i get.
```

erwin@erwin-linux:~$ sudo mount -t vfat /dev/sdc1 /media/USB -o umask=000
mount: special device /dev/sdc1 does not exist

```

BUT

It turns out that Ubuntu isn't the problem and that the harddisk working when it was connected at boottime was a fluke.

When i tried again the harddisk wasn't even recognised at boot time.
So i dug up an old sitecom case and a 6.4 GB harddisk. Put it together, connected that one and sure enough, that one was seen and mounted by ubuntu without any problems.

Guess i have to find out what&#347; wrong with my other drive.

FOUND IT.

Turns out windows has been more forgiving (to an idiot) then linux.
The external harddisk had always worked without a problem when it was used under windows.
But when i opened it to see if i could find a problem, cables or anything i found out i hadn't set the jumper correctly when i installed the harddisk. It was set to master with slave instead of single master. I changed the jumper and reconnected the drive. Now Ubuntu sees it right away.
I wouldn't be supprised if this also solves my problem that some files aren't visible when it's connected as a networkdrive.

---

