---
title: "How do I add a new ssd to my PC?"
date: 2020-07-30
forum: Hardware
---

### Post by robert48 on 2020-07-30
Hi

I have Ubuntu Desktop 20.04.1 LTS running on my PC. I want to add a new ssd to take backups. The new SanDisk Plus 240GB ssd has been physically installed and Disks can see it. I can see it in Files. However when I try to create a folder I receive an error message saying that I do not have permission.

How do I give myself permission to use the ssd please?

---

### Post by CatKiller on 2020-07-30
The term that you're after to help you find what you want is **mounting**, which means to attach the filesystem contained on that drive to somewhere in the filesystem tree.

There are already a bajillion posts and articles on how to do it and different storage strategies you might choose to use. Have a look through some of them and post back if there's a particular part you're struggling with.

---

### Post by oldfred on 2020-07-30
Have you partitioned it? With gpt?
I also prefer to have an ESP as first partition, just in case later I want an install on the drive even if planned as a data only drive. But I typically but at least a smaller Ubuntu install for emergency use on every drive, even my larger data/backup flash drives.

Post this:
sudo parted -l

Best to mount in fstab if an internal drive, but not use Disks as its defaults are not best particularly for SSDs.

I do not like Disks as it may not use correct parameters. Better to use template/example and adjust for your specifics
[https://askubuntu.com/questions/164926/how-to-make-partitions-mount-at-startup](https://askubuntu.com/questions/164926/how-to-make-partitions-mount-at-startup)
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.

For SSD I use noatime, and for HDD, use relatime as a parameter.

---

### Post by robert48 on 2020-07-30
sudo parted -l returns this for the subject concerned:-

Model: ATA SanDisk SSD PLUS (scsi)
Disk /dev/sdc: 240GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End    Size    Type      File system     Flags
 1      1049kB  235GB  235GB   primary   ext4
 2      235GB   240GB  4799MB  extended
 5      235GB   240GB  4798MB  logical   linux-swap(v1)

---

### Post by rsteinmetz70112 on 2020-07-30
Have you mounted /dev/sdc1? or better mounted yet it using UUID and including that in the fstab?
try```
$ sudo lsblk
$ sudo blkid
```

---

### Post by robert48 on 2020-07-30
lsblk returns:

```

NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0    7:0    0 113.4M  1 loop /snap/audacity/666
loop1    7:1    0 113.4M  1 loop /snap/audacity/675
loop2    7:2    0 158.4M  1 loop /snap/chromium/1235
loop3    7:3    0 158.4M  1 loop /snap/chromium/1244
loop4    7:4    0  24.1M  1 loop /snap/gnome-calendar/123
loop5    7:5    0  96.5M  1 loop /snap/core/9436
loop6    7:6    0    97M  1 loop /snap/core/9665
loop7    7:7    0   7.9M  1 loop /snap/evince/434
loop8    7:8    0    55M  1 loop /snap/core18/1880
loop9    7:9    0    55M  1 loop /snap/core18/1754
loop10   7:10   0     8M  1 loop /snap/evince/483
loop11   7:11   0   4.2M  1 loop /snap/network-manager/550
loop12   7:12   0  43.2M  1 loop /snap/snap-store/415
loop13   7:13   0   4.2M  1 loop /snap/network-manager/564
loop14   7:14   0   291M  1 loop /snap/vlc/1620
loop15   7:15   0  62.1M  1 loop /snap/gtk-common-themes/1506
loop16   7:16   0   140K  1 loop /snap/gtk2-common-themes/13
loop17   7:17   0   132K  1 loop /snap/gtk2-common-themes/9
loop18   7:18   0 290.4M  1 loop /snap/vlc/1700
loop19   7:19   0  54.8M  1 loop /snap/gtk-common-themes/1502
loop20   7:20   0  93.9M  1 loop /snap/mpv/1
loop21   7:21   0 177.2M  1 loop /snap/skype/137
loop22   7:22   0 255.6M  1 loop /snap/gnome-3-34-1804/36
loop23   7:23   0   880K  1 loop /snap/gnome-mines/271
loop24   7:24   0  24.1M  1 loop /snap/gnome-calendar/132
loop25   7:25   0   2.2M  1 loop /snap/gnome-system-monitor/145
loop26   7:26   0 177.2M  1 loop /snap/skype/139
loop27   7:27   0  49.8M  1 loop /snap/snap-store/467
loop28   7:28   0 416.2M  1 loop /snap/libreoffice/180
loop29   7:29   0 255.6M  1 loop /snap/gnome-3-34-1804/33
loop30   7:30   0   9.1M  1 loop /snap/canonical-livepatch/95
loop31   7:31   0   6.5M  1 loop /snap/gnome-clocks/257
loop32   7:32   0   9.1M  1 loop /snap/canonical-livepatch/94
loop33   7:33   0 160.2M  1 loop /snap/gnome-3-28-1804/116
loop34   7:34   0 161.4M  1 loop /snap/gnome-3-28-1804/128
loop35   7:35   0   416M  1 loop /snap/libreoffice/183
loop36   7:36   0 163.7M  1 loop /snap/spotify/41
loop37   7:37   0   6.3M  1 loop /snap/gnome-clocks/261
loop38   7:38   0  21.1M  1 loop /snap/python36-jamesh/20
loop39   7:39   0   2.2M  1 loop /snap/gnome-system-monitor/148
sda      8:0    0 111.8G  0 disk 
&#9500;&#9472;sda1   8:1    0   107G  0 part /
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9492;&#9472;sda5   8:5    0   4.8G  0 part [SWAP]
sdb      8:16   0 111.8G  0 disk /home
sdc      8:32   0 223.6G  0 disk 
&#9500;&#9472;sdc1   8:33   0 219.1G  0 part /media/bob/240ssd
&#9500;&#9472;sdc2   8:34   0     1K  0 part 
&#9492;&#9472;sdc5   8:37   0   4.5G  0 part 
sdd      8:48   0 596.2G  0 disk 
&#9492;&#9472;sdd1   8:49   0 596.2G  0 part 
sr0     11:0    1  1024M  0 rom 

```

sudo blkid returns:
```

/dev/sda5: UUID="49db1e47-e52b-45fc-a6a4-b61fc9785ec8" TYPE="swap" PARTUUID="00025a32-05"
/dev/sda1: UUID="7b44d51c-e989-40d7-bc7b-b30d802ac58e" TYPE="ext4" PARTUUID="00025a32-01"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/sdb: LABEL="Home460" UUID="4e7f8f39-381f-44ff-bf25-50eb99954250" TYPE="ext4"
/dev/sdc1: LABEL="240ssd" UUID="0fc44b5b-1f54-40e1-84f6-2496a325a8e2" TYPE="ext4" PARTUUID="21b02785-01"
/dev/sdc5: UUID="74913805-dad1-47af-9cae-b4e142018ffc" TYPE="swap" PARTUUID="21b02785-05"
/dev/sdd1: LABEL="VideoHD" UUID="1d278a93-d076-4f66-9d75-d559b9398df5" SEC_TYPE="ext2" TYPE="ext3" PARTUUID="00091c1e-01"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"
/dev/loop12: TYPE="squashfs"
/dev/loop13: TYPE="squashfs"
/dev/loop14: TYPE="squashfs"
/dev/loop15: TYPE="squashfs"
/dev/loop16: TYPE="squashfs"
/dev/loop17: TYPE="squashfs"
/dev/loop18: TYPE="squashfs"
/dev/loop19: TYPE="squashfs"
/dev/loop20: TYPE="squashfs"
/dev/loop21: TYPE="squashfs"
/dev/loop22: TYPE="squashfs"
/dev/loop23: TYPE="squashfs"
/dev/loop24: TYPE="squashfs"
/dev/loop25: TYPE="squashfs"
/dev/loop26: TYPE="squashfs"
/dev/loop27: TYPE="squashfs"
/dev/loop28: TYPE="squashfs"
/dev/loop29: TYPE="squashfs"
/dev/loop30: TYPE="squashfs"
/dev/loop31: TYPE="squashfs"
/dev/loop32: TYPE="squashfs"
/dev/loop33: TYPE="squashfs"
/dev/loop34: TYPE="squashfs"
/dev/loop35: TYPE="squashfs"
/dev/loop36: TYPE="squashfs"
/dev/loop37: TYPE="squashfs"
/dev/loop38: TYPE="squashfs"
/dev/loop39: TYPE="squashfs"

```

---

### Post by robert48 on 2020-07-30
sudo fstab returns:
```

 / was on /dev/sda1 during installation
UUID=7b44d51c-e989-40d7-bc7b-b30d802ac58e /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb during installation
UUID=4e7f8f39-381f-44ff-bf25-50eb99954250 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=49db1e47-e52b-45fc-a6a4-b61fc9785ec8 none            swap    sw              0       0
/dev/sdd /mnt/sdd ext3 nosuid,nodev,nofail,x-gvfs-show 0 0
/dev/disk/by-uuid/196ff6e7-4b54-4537-9fa0-3247d6a0c755 /mnt/196ff6e7-4b54-4537-9fa0-3247d6a0c755 auto nosuid,nodev,nofail,x-gvfs-show 0 0
/dev/disk/by-uuid/c5fb2af6-f1f1-4b36-b532-ab391efec138 /mnt/c5fb2af6-f1f1-4b36-b532-ab391efec138 auto nosuid,nodev,nofail,x-gvfs-show,x-gvfs-name=bbussd 0 0
/dev/disk/by-uuid/UUID="0fc44b5b-1f54-40e1-84f6-2496a325a8e2" /mnt/240ssd auto nosuid,nodev,noatime,nofail,x-gvfs-show,x-gvfs-icon=bbackup,x-gvfs-name=bbackup 0

```

---

### Post by TheFu on 2020-07-30
Where do you want to mount it?  If you **sudo mkdir /Backups**, then add this line to the fstab:
```
UUID=0fc44b5b-1f54-40e1-84f6-2496a325a8e2 /Backups           ext4    defaults        0       2
```
Run 
```
sudo systemctl daemon-reload
sudo mount -a

```
Then it will be mounted to /Backups
Next you probably want to make a few subdirectories for each userid ... or not.  If you use a real backup tool, that runs from crontab using the root account, you are done. Just configure that to point at /Backups for the TARGET.  If you are doing what I call weenie backups, individual user stuff, or worse, using a file copy method, then you'll need to **chown /Backups** to your username:groupname.

Completely, 100% unrelated:   BTW, the line below looks incorrect, since partitions are mounted, not entire HDDs.  I suppose there are exceptions, but those go against the best-practice recommendations.
```
/dev/sdd /mnt/sdd ext3 nosuid,nodev,nofail,x-gvfs-show 0 0
```

One last thing.  Using an SSD for backup storage seems highly extravagant when a 2TB HDD is $45. Certainly there is a better use for that SSD than swap and backups.

---

### Post by robert48 on 2020-07-30
Thank you all, points noted, fstab edited and cleaned up, including sdd (thank you TheFu)

I completely erased the ssd drive and used Disks, with oldfreds suggestion of ```
noatime
``` added to the options, set up the mount point in /mnt/'UUID' using rsteinmetz70112 suggestion to find the UUID string with ```
sudo blkid 
```and then set up a backup directory called bobsbackups using Files when the drive was mounted. Very impressed with the advancement of the GUI applications but recommend anybody following look at the helpful comments above to understand what is going on under the hood, in particular the fstab file and how to get information from the drive.

Backing up now as I write this.

Many thanks for all your help!

---

### Post by TheFu on 2020-07-30
All the other people deserve the credit for having you run the commands to get the needed info.

Disks has lots of problems.  Better to use **gparted** instead and always manually mount storage via the fstab. Sometimes the resulting stuff from the gnome-disks program aren't good.  For some file system types, the result is bad.

---

