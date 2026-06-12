---
title: "Raid1 install error, umount md0, input/output error"
date: 2019-10-01
forum: Hardware
---

### Post by glenerik on 2019-10-01
My recently installed raid drives disappeared after 

```


umount /dev/md0 
sudo mdadm --stop /dev/md0


```

 how do I start from zero and reformat them? It seems like their disappearance also caused my server to have issues, I cannot even run vim

```
-bash: /usr/bin/vim: Input/output error
```

and even though I was able to shutdown -r the server, now I cant:

```

$ sudo shutdown now
Failed to open /dev/initctl: No such device or address
Failed to talk to init daemon.

```

**How I got here:**

I tried configuring two hard drives as raid1 following this tutorial:

[https://www.linuxbabe.com/linux-server/linux-software-raid-1-setup](https://www.linuxbabe.com/linux-server/linux-software-raid-1-setup)

However, I am using ubuntu server 18.04 so Linux RAID autodetect (fd) was not an option. I selected 29 for Linux RAID.

I setup the raid and it looked fine like the tutorial until I tried to create a directory in /mnt/raid1. It would not let me due to permissions and it would not let me chown /mnt/raid1. Running ```
sudo fsdisk -l
``` showed the following message on one of the new drives:

```
The backup GPT table is corrupt, but the primary appears OK, so that will be used.
```

The sudo fsdisk-l output was the same as this post [https://ubuntuforums.org/showthread.php?t=2361339](https://ubuntuforums.org/showthread.php?t=2361339), so I did:

```
sudo umount /dev/md0
sudo mdadm --stop /dev/md0
```

Then I could no longer see or access the /dev/sdb1 /dev/sdc1 and reassembling md0 failed.

The sudo fdisk -l output now shows all of my original harddrive's partitions and does not show the two new drives. It used to not show all of these partitions:

```

$ sudo fdisk -l
Disk /dev/loop0: 212.1 MiB, 222388224 bytes, 434352 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop1: 3.1 MiB, 3248128 bytes, 6344 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop2: 88.7 MiB, 92983296 bytes, 181608 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop3: 89 MiB, 93327360 bytes, 182280 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop4: 217.8 MiB, 228388864 bytes, 446072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop5: 3.1 MiB, 3252224 bytes, 6352 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop6: 11.7 MiB, 12242944 bytes, 23912 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: AF308587-0A23-464F-9CF7-1C3D17ADA860


Device       Start        End    Sectors   Size Type
/dev/sda1     2048       4095       2048     1M BIOS boot
/dev/sda2     4096    2101247    2097152     1G Linux filesystem
/dev/sda3  2101248 1953521663 1951420416 930.5G Linux filesystem




Disk /dev/mapper/ubuntu--vg-ubuntu--lv: 337 GiB, 361842606080 bytes, 706723840 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/mapper/ubuntu--vg-lv--ml: 434.8 GiB, 466876366848 bytes, 911867904 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```

---

### Post by glenerik on 2019-10-01
My original filesystem is now in read-only mode. Any ideas?

bash: cannot create temp file for here-document: Read-only file system

---

