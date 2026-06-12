---
title: "Expanding an iSCSI multipath device."
date: 2018-04-17
forum: Hardware
---

### Post by doctor-kisow on 2018-04-17
[SIZE=3][FONT=arial][COLOR=#111111]I have a production multi-pathed iSCSI SAN (Dell MD3200i) with 40Tib of storage. This SAN was recently upgraded with an additional shelf expanding it to 80Tib. This storage is presented to an ***Ubuntu 14.04.5 LTS*** server as part of an open-iscsi and multipath configuration; this storage is presented to the server on */dev/mapper/mpath0-part1:*[/COLOR]

Partition Information:
[/FONT]```
# [B]parted -l
[/B]Model: VMware Virtual disk (scsi)
Disk /dev/sda: 172GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  256MB  255MB  primary   ext2         boot
 2      257MB   172GB  172GB  extended
 5      257MB   172GB  172GB  logical                lvm

Model: DELL MD32xxi (scsi)
Disk /dev/sdb: 88.0TB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      1049kB  88.0TB  88.0TB  ext4         primary

Model: DELL MD32xxi (scsi)
Disk /dev/sdc: 88.0TB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      1049kB  88.0TB  88.0TB  ext4         primary

Model: DELL MD32xxi (scsi)
Disk /dev/sdd: 88.0TB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      1049kB  88.0TB  88.0TB  ext4         primary

Model: DELL MD32xxi (scsi)
Disk /dev/sde: 88.0TB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      1049kB  88.0TB  88.0TB  ext4         primary

Model: DELL MD32xxi (scsi)
Disk /dev/sdf: 88.0TB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      1049kB  88.0TB  88.0TB  ext4         primary

Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/mpath0-part1: 88.0TB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  88.0TB  88.0TB  ext4

Model: Linux device-mapper (multipath) (dm)
Disk /dev/mapper/mpath0: 88.0TB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      1049kB  88.0TB  88.0TB  ext4         primary

Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/pathology--linux--fileserver--vg-swap_1: 8586MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  8586MB  8586MB  linux-swap(v1)

Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/pathology--linux--fileserver--vg-root: 163GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  163GB  163GB  ext4

Model: DELL MD32xxi (scsi)
Disk /dev/sdg: 88.0TB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      1049kB  88.0TB  88.0TB  ext4         primary

Model: DELL MD32xxi (scsi)
Disk /dev/sdh: 88.0TB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      1049kB  88.0TB  88.0TB  ext4         primary

Model: DELL MD32xxi (scsi)
Disk /dev/sdi: 88.0TB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name     Flags
 1      1049kB  88.0TB  88.0TB  ext4         primary
```
[FONT=arial]
Multipath Configuration File:
[/FONT]```
# [B]cat /etc/multipath.conf
[/B]defaults
{
        verbosity 2
        wwids_file /etc/multipath/wwids
        max_fds 8192
        user_friendly_names yes
        #user_friendly_names yes
        #path_grouping_policy multibus
        #path_checker readsector0
        #polling_interval 3
        #path_selector "round-robin 0"
        #failback immediate
        #features "0"
        #no_path_retry 1
}

blacklist
{
        devnode "^(ram|raw|loop|fd|md|sr|scd|st)[0-9]*"
        devnode "^hda"
        devnode "^sda"
        devnode "^dcssblk[0-9]*"
        devnode "^cciss!c[0-9]d[0-9]*"
        devnode "^(ram|raw|loop|fd|md|sr|scd|st)[0-9]*"
        devnode "^hd[a-z]"
        devnode "^dcssblk[0-9]*"
        devnode "^cciss!c[0-9]d[0-9]*"
        device
        {
                vendor "*"
                product "Universal Xport"
        }
}

blacklist_exceptions
{
        devnode "^mpath*"
        devnode "^dm-*"
}

devices
{
        device
        {
                vendor                  "DELL"
                product                 "MD32xxi"
                path_grouping_policy    group_by_prio
                #getuid_callout         "/lib/udev/scsi_id --whitelisted --device=/dev/%n"
                path_selector           "round-robin 0"
                path_checker            rdac
                checker                 rdac
                features                "2 pg_init_retries 50"
                hardware_handler        "1 rdac"
                prio                    rdac
                failback                immediate
                no_path_retry           30
                rr_min_io               100
        }
}

multipaths
{
        multipath
        {
                # iSCSI WWID retreived with: /lib/udev/scsi_id --whitelisted --device=/dev/sdj
                #wwid
                #3644a842000016bfd000002a654bf22ad
                #alias nfs
                device
                {
                        vendor          DELL
                        product         MD3200i
                }
        }
}

```
[FONT=arial]
Multipath List:
```
# **multipath -ll**
mpath0 (3644a842000016bfd000002a654bf22ad) dm-2 DELL    ,MD32xxi
size=**80T** features='3 queue_if_no_path pg_init_retries 50' hwhandler='1 rdac' wp=rw
|-+- policy='round-robin 0' prio=6 status=active
| |- 3:0:0:1  sdg  8:96  active ready running
| |- 4:0:0:1  sdi  8:128 active ready running
| |- 5:0:0:1  sdd  8:48  active ready running
| `- 8:0:0:1  sdb  8:16  active ready running
`-+- policy='round-robin 0' prio=1 status=enabled
  |- 10:0:0:1 sdc  8:32  active ghost running
  |- 6:0:0:1  sdh  8:112 active ghost running
  |- 7:0:0:1  sdf  8:80  active ghost running
  `- 9:0:0:1  sde  8:64  active ghost running
```
[COLOR=#111111]
Listing the block devices shows the disk and partitions have been expanded to the SAN volume size. With the disk being (dm-2) or */dev/dm-2* and the partition being (dm-3) or */dev/dm-3*. Both can see the 80Tib of storage:[/COLOR]

```
# **lsblk**
NAME                                               MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda                                                  8:0    0   160G  0 disk
&#9500;&#9472;sda1                                               8:1    0   243M  0 part  /boot
&#9500;&#9472;sda2                                               8:2    0     1K  0 part
&#9492;&#9472;sda5                                               8:5    0 159.8G  0 part
  &#9500;&#9472;pathology--linux--fileserver--vg-root (dm-0)   252:0    0 151.7G  0 lvm   /
  &#9492;&#9472;pathology--linux--fileserver--vg-swap_1 (dm-1) 252:1    0     8G  0 lvm   [SWAP]
sdb                                                  8:16   0    80T  0 disk
&#9492;&#9472;mpath0 (dm-2)                                    252:2    0    80T  0 mpath
  &#9492;&#9472;mpath0-part1 (dm-3)                            252:3    0    80T  0 part /Pathology_Lab
sdc                                                  8:32   0    80T  0 disk
&#9492;&#9472;mpath0 (dm-2)                                    252:2    0    80T  0 mpath
  &#9492;&#9472;mpath0-part1 (dm-3)                            252:3    0    80T  0 part /Pathology_Lab
sdd                                                  8:48   0    80T  0 disk
&#9492;&#9472;mpath0 (dm-2)                                    252:2    0    80T  0 mpath
  &#9492;&#9472;mpath0-part1 (dm-3)                            252:3    0    80T  0 part /Pathology_Lab
sde                                                  8:64   0    80T  0 disk
&#9492;&#9472;mpath0 (dm-2)                                    252:2    0    80T  0 mpath
  &#9492;&#9472;mpath0-part1 (dm-3)                            252:3    0    80T  0 part /Pathology_Lab
sdf                                                  8:80   0    80T  0 disk
&#9492;&#9472;mpath0 (dm-2)                                    252:2    0    80T  0 mpath
  &#9492;&#9472;mpath0-part1 (dm-3)                            252:3    0    80T  0 part /Pathology_Lab
sdg                                                  8:96   0    80T  0 disk
&#9492;&#9472;mpath0 (dm-2)                                    252:2    0    80T  0 mpath
  &#9492;&#9472;mpath0-part1 (dm-3)                            252:3    0    80T  0 part /Pathology_Lab
sdh                                                  8:112  0    80T  0 disk
&#9492;&#9472;mpath0 (dm-2)                                    252:2    0    80T  0 mpath
  &#9492;&#9472;mpath0-part1 (dm-3)                            252:3    0    80T  0 part /Pathology_Lab
sdi                                                  8:128  0    80T  0 disk
&#9492;&#9472;mpath0 (dm-2)                                    252:2    0    80T  0 mpath
  &#9492;&#9472;mpath0-part1 (dm-3)                            252:3    0    80T  0 part /Pathology_Lab
sr0                                                 11:0    1  1024M  0 rom
```
[COLOR=#111111]
When mounted, the disk only shows 40Tib:[/COLOR]

```
# **df -h**
Filesystem                Size  Used Avail Use% Mounted on
udev                      7.9G   12K  7.9G   1% /dev
tmpfs                     1.6G  1.4M  1.6G   1% /run
/dev/dm-0                 150G  7.0G  135G   5% /
none                      4.0K     0  4.0K   0% /sys/fs/cgroup
none                      5.0M     0  5.0M   0% /run/lock
none                      7.9G  152K  7.9G   1% /run/shm
none                      100M   40K  100M   1% /run/user
/dev/sda1                 236M  105M  119M  47% /boot
[COLOR=#ff0000]/dev/mapper/mpath0-part1   37T   35T  299G 100% /Pathology_Lab[/COLOR]
```
[COLOR=#111111]
The command **e2fsck -f  -y -v -C 0 /dev/mapper/mpath0-part1** successfully runs without error; however if I run the command individually on /dev/sdb1 -- /dev/sdi1 I receive a superblock error[/COLOR][/FONT][FONT=arial][COLOR=#111111]:
[/COLOR][/FONT]
```
# **e2fsck -f -y -v -C 0 /dev/mapper/mpath0-part1**
e2fsck 1.42.9 (4-Feb-2014)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

     1057830 inodes used (0.17%, out of 610390016)
       20331 non-contiguous files (1.9%)
         454 non-contiguous directories (0.0%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 937261/15986/2
  9199763793 blocks used (94.20%, out of 9766230528)
           0 bad blocks
        4548 large files


      736177 regular files
      115426 directories
           0 character device files
           0 block device files
           0 fifos
         397 links
      206218 symbolic links (104572 fast symbolic links)
           0 sockets
------------
     1058218 files
```

```
# **e2fsck -f -y -v -C 0 /dev/sdb1**
e2fsck 1.42.9 (4-Feb-2014)
e2fsck: No such file or directory while trying to open /dev/sdb1
Possibly non-existent device?
```

[FONT=arial][COLOR=#111111]W[/COLOR][/FONT][COLOR=#111111][FONT=arial]hen I looked up these errors it appears as though I "may" have to rebuild this disk from scratch.

[/FONT][/COLOR]
[FONT=arial][COLOR=#111111]The command **resize2fs -p /dev/mapper/mpath0-part1** just hangs and nothing shows in the logs.[/COLOR]
[COLOR=#111111]I realize this could take a long time however nothing is indicating that it is expanding or even running except for the processor consumption.
[/COLOR]
[COLOR=#111111]Anyone able to point me in the right direction?[/COLOR][/FONT][/SIZE]

---

### Post by doctor-kisow on 2018-04-17
[SIZE=3][FONT=arial]So after some research, I decided to look and ensure I truly have an ext4 file-system. I ran the following command against my device and found this:

```
# [COLOR=#242729]**file -s /dev/mapper/mpath0-path1**
[/COLOR][COLOR=#242729]/dev/mapper/mpath0-path1: Linux rev 1.0 **ext4** filesystem data [/COLOR][COLOR=#ff0000]**(needs journal recovery)**[/COLOR][COLOR=#242729] (extents) (large files) (huge files)[/COLOR]
```

After searching for the "correct" way to do a journal recovery I took the **/dev/mapper/mpath0-part1 **device offline by commenting out the device in my **/etc/fstab** and rebooting; then I ran:

```
[COLOR=#000000]# [/COLOR][B]e2fsck -f -y -v -C 0 /dev/mapper/mpath0-part1
[/B]e2fsck 1.42.9 (4-Feb-2014)
[COLOR=#0000ff]**/dev/mapper/mpath0-part1: recovering journal**[/COLOR]
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

     1057830 inodes used (0.17%, out of 610390016)
       20331 non-contiguous files (1.9%)
         454 non-contiguous directories (0.0%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 937261/15986/2
  9199763793 blocks used (94.20%, out of 9766230528)
           0 bad blocks
        4548 large files


      736177 regular files
      115426 directories
           0 character device files
           0 block device files
           0 fifos
         397 links
      206218 symbolic links (104572 fast symbolic links)
           0 sockets
------------
     1058218 files

```

After journal recovery the device looks like this:

```
# [B]file -s /dev/mapper/mpath0-part1
[/B]/dev/mapper/mpath0-part1: Linux rev 1.0 ext4 filesystem data, [COLOR=#ff0000]**UUID=83a212e2-a551-42d4-b746-1549d2630c4c**[/COLOR] (extents) [COLOR=#ff0000]**(64bit)**[/COLOR] (large files) (huge files)

```[/FONT][/SIZE]

---

