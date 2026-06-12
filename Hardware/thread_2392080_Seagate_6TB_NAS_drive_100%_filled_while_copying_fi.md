---
title: "Seagate 6TB NAS drive 100% filled while copying file, reboot fixes."
date: 2018-05-16
forum: Hardware
---

### Post by roxsen on 2018-05-16
Hey everyone,

Not sure if im doing something wrong here, I may as well be new to Ubuntu/Linux at this point. I used to use Arch but my skills are EXTREMELY rusty!

Anyways the issue is that I am setting up a small home server for plex, media, fileshares etc and in doing so I have installed a Seagate NAS drive everything seems to go okay, I have it in fstab and it mounts to /media/Vault.
it is formatted in ext4.

When I run df -h it shows me I am using about 6% (I have some existing files on there) 
Now when I want to copy anything to the drive the system locks up and lags really badly, when I finally get a chance to run df it shows that I am using 100% of that drive, untill it crashes out and reboots then running df again shows that it is back to 6%

df -h output
```
mike@homeserver:~$ df -hFilesystem      Size  Used Avail Use% Mounted on
udev            3.9G     0  3.9G   0% /dev
tmpfs           786M  1.2M  785M   1% /run
/dev/sda2       110G  9.7G   94G  10% /
tmpfs           3.9G   16K  3.9G   1% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/loop0       87M   87M     0 100% /snap/core/4571
/dev/loop1       87M   87M     0 100% /snap/core/4486
/dev/sda1       511M  4.6M  507M   1% /boot/efi
/dev/sdb2       4.6T  241G  4.1T   6% /media/Vault
tmpfs           786M     0  786M   0% /run/user/1000

```

fstab file
```
UUID=027c2bcf-5746-11e8-aa47-c860007a061a / ext4 defaults 0 0UUID=69B9-0A0B /boot/efi vfat defaults 0 0
/swap.img       none    swap    sw      0       0
UUID=0c3634ef-b2ac-4858-a190-6227bc7ce335 /media/Vault ext4 defaults 0 0

```

lsblk output
```
mike@homeserver:~$ lsblkNAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0    7:0    0  86.6M  1 loop /snap/core/4571
loop1    7:1    0  86.6M  1 loop /snap/core/4486
sda      8:0    0 111.8G  0 disk
&#9500;&#9472;sda1   8:1    0   512M  0 part /boot/efi
&#9492;&#9472;sda2   8:2    0 111.3G  0 part /
sdb      8:16   0   5.5T  0 disk
&#9500;&#9472;sdb1   8:17   0   900G  0 part
&#9492;&#9472;sdb2   8:18   0   4.6T  0 part /media/Vault

```

trimmed fdisk -l output
```
Disk /dev/sdb: 5.5 TiB, 6001175126016 bytes, 11721045168 sectorsUnits: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 8792F0A2-43DC-11E8-9178-C860007A061A


Device          Start         End    Sectors  Size Type
/dev/sdb1        2048  1887485951 1887483904  900G Microsoft basic data
/dev/sdb2  1887485952 11721045134 9833559183  4.6T Linux filesystem

```

Any thoughts?
thanks in advance.

---

