---
title: "Single RAID1 disk - mounting via USB"
date: 2024-01-28
forum: Hardware
---

### Post by divine-wind on 2024-01-28
Hi

I have a single 4TB drive rescued from a dead Debian9 server

The drive contains data only and was part of a RAID1 array and now sits in a USB caddy attached to a headless Ubuntu 22.04 server

```

#fdisk -l
[COLOR=#000000][FONT=&amp]Disk /dev/sdc: 3.64 TiB, 4000787030016 bytes, 7814037168 sectors[/FONT][/COLOR][COLOR=#2FFF12][FONT=&amp][COLOR=#000000]Disk model: EFRX-68N32N0    [/COLOR][/FONT][/COLOR]
[COLOR=#2FFF12][FONT=&amp][COLOR=#000000]Units: sectors of 1 * 512 = 512 bytes[/COLOR][/FONT][/COLOR]
[COLOR=#2FFF12][FONT=&amp][COLOR=#000000]Sector size (logical/physical): 512 bytes / 4096 bytes[/COLOR][/FONT][/COLOR]
[COLOR=#2FFF12][FONT=&amp][COLOR=#000000]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/COLOR][/FONT][/COLOR]
[COLOR=#2FFF12][FONT=&amp][COLOR=#000000]Disklabel type: gpt[/COLOR][/FONT][/COLOR]
[COLOR=#2FFF12][FONT=&amp][COLOR=#000000]Disk identifier: 5DAF00AF-DD46-4C9C-A259-D72F635A8D10[/COLOR][/FONT][/COLOR]
[COLOR=#2FFF12][FONT=&amp][COLOR=#000000]
[/COLOR][/FONT][/COLOR]
[COLOR=#00FF00][FONT=&amp][COLOR=#000000]Device     Start        End    Sectors  Size Type[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]/dev/sdc1 [/FONT][FONT=&amp]2048 7814035455 7814033408[/FONT][FONT=&amp]3.6T Linux RAID[/FONT][/COLOR]
```

but ..

```
#[COLOR=#000000][FONT=&amp]sudo mount -t ext4 /dev/sdc1 /mnt/xtunes
[/FONT][FONT=&amp]mount: /mnt/xtunes: /dev/sdc1 already mounted or mount point busy[/FONT][/COLOR]
```

and ..

```
#[COLOR=#000000][FONT=&amp]sudo mdadm --examine /dev/sdc1[/FONT][/COLOR][COLOR=#2FFF12][FONT=&amp][COLOR=#000000]:[/COLOR][/FONT][/COLOR]
[COLOR=#2FFF12][FONT=&amp][COLOR=#000000]          Magic : a92b4efc[/COLOR][/FONT][/COLOR]
[COLOR=#2FFF12][FONT=&amp][COLOR=#000000]        Version : 1.2[/COLOR][/FONT][/COLOR]
[COLOR=#2FFF12][FONT=&amp][COLOR=#000000]    Feature Map : 0x1[/COLOR][/FONT][/COLOR]
[COLOR=#2FFF12][FONT=&amp][COLOR=#000000]     Array UUID : c73ad58e:2a40147a:09e81df6:2566dd07[/COLOR][/FONT][/COLOR]
[COLOR=#2FFF12][FONT=&amp][COLOR=#000000]           Name : roonserver:0[/COLOR][/FONT][/COLOR]
[COLOR=#2FFF12][FONT=&amp][COLOR=#000000]  Creation Time : Sun Jun 10 19:02:55 2018[/COLOR][/FONT][/COLOR]
[COLOR=#2FFF12][FONT=&amp][COLOR=#000000]     Raid Level : raid1[/COLOR][/FONT][/COLOR]
[COLOR=#2FFF12][FONT=&amp][COLOR=#000000]   Raid Devices : 2[/COLOR][/FONT][/COLOR]
[COLOR=#2FFF12][FONT=&amp][COLOR=#000000]
[/COLOR][/FONT][/COLOR]
[COLOR=#2FFF12][FONT=&amp][COLOR=#000000] Avail Dev Size : 7813771264 sectors (3.64 TiB 4.00 TB)[/COLOR][/FONT][/COLOR]
[COLOR=#2FFF12][FONT=&amp][COLOR=#000000]     Array Size : 3906885632 KiB (3.64 TiB 4.00 TB)[/COLOR][/FONT][/COLOR]
[COLOR=#2FFF12][FONT=&amp][COLOR=#000000]    Data Offset : 262144 sectors[/COLOR][/FONT][/COLOR]
[COLOR=#2FFF12][FONT=&amp][COLOR=#000000]   Super Offset : 8 sectors[/COLOR][/FONT][/COLOR]
[COLOR=#2FFF12][FONT=&amp][COLOR=#000000]   Unused Space : before=262056 sectors, after=0 sectors[/COLOR][/FONT][/COLOR]
[COLOR=#2FFF12][FONT=&amp][COLOR=#000000]          State : clean[/COLOR][/FONT][/COLOR]
[COLOR=#2FFF12][FONT=&amp][COLOR=#000000]    Device UUID : cb590e0b:1222edb0:cc227568:ca3e84cf[/COLOR][/FONT][/COLOR]
[COLOR=#2FFF12][FONT=&amp][COLOR=#000000]
[/COLOR][/FONT][/COLOR]
[COLOR=#2FFF12][FONT=&amp][COLOR=#000000]Internal Bitmap : 8 sectors from superblock[/COLOR][/FONT][/COLOR]
[COLOR=#2FFF12][FONT=&amp][COLOR=#000000]    Update Time : Sun Jan 28 14:29:28 2024[/COLOR][/FONT][/COLOR]
[COLOR=#2FFF12][FONT=&amp][COLOR=#000000]  Bad Block Log : 512 entries available at offset 72 sectors[/COLOR][/FONT][/COLOR]
[COLOR=#2FFF12][FONT=&amp][COLOR=#000000]       Checksum : 1d3bc8b9 - correct[/COLOR][/FONT][/COLOR]
[COLOR=#2FFF12][FONT=&amp][COLOR=#000000]         Events : 217230[/COLOR][/FONT][/COLOR]
[COLOR=#2FFF12][FONT=&amp][COLOR=#000000]
[/COLOR][/FONT][/COLOR]
[COLOR=#2FFF12][FONT=&amp][COLOR=#000000]
[/COLOR][/FONT][/COLOR]
[COLOR=#2FFF12][FONT=&amp][COLOR=#000000]   Device Role : Active device 0[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Array State : AA ('A' == active, '.' == missing, 'R' == replacing)[/FONT][/COLOR]
```

Is it possible to mount this partition so I can rescue the data please?


Many thanks for any help

---

### Post by TheFu on 2024-01-29
You need to assemble a partial array. That will create a RAID device with a file system that can be mounted.  I'd have to look up the mdadm commands in the mdadm manpage, so I figure you can do that yourself just as easily.

I'm assuming this was a software-RAID array and created using mdadm. If that isn't the situation, ignore what I've posted. IDK. If Fake-RAID was used, you will probably need an identical motherboard with identical disk controller, to gain any access.

---

### Post by MAFoElffen on 2024-01-30
You should be able to do
```

mdadm --assemble /dev/md1 --run /dev/sdc1

```
Adjust to whatever the md device name. The "--run" option there tells it not to abort if there is a missing device (the other half of the RAID1)... So that way it can come up as half of the RAID1.

Then you can backup what you need to get off there, or recreate the other half of that to another drive... By adding in a new drive via
```

sudo mdadm --manage /dev/md1 --add /dev/sdd1

```
Or whatever your plan is from here....

TheFu talked me out of working more on the mdmadm-gui Project I was working on... Enough said on that. LOL.

---

