---
title: "Strange disk issue"
date: 2021-12-17
forum: Hardware
---

### Post by Andrew_Welham on 2021-12-17
Dear All,
I'm running a fully patched ubuntu 20.04 server with a 14Tb internal sata disk + NVME  boot drive and then 5 external 8TB usb disks

Recently i have been getting high IOwait near 100% and the system has been hanging. Expecting a disk failure i started to look for errors. No disk is reporting errors even with smartctl. A couple of fsck required as the system effectivly hung while writing (although the system was operable as long as the usb disks were not accessed,

I have noticed the following in the logs
```
Dec 13 16:42:46 servername kernel: [    4.089857] sd 9:0:0:0: [sdf] Very big device. Trying to use READ CAPACITY(16).
Dec 13 16:42:46 servername kernel: [    4.091653] sd 9:0:0:0: [sdf] 15628053167 512-byte logical blocks: (8.00 TB/7.28 TiB)
Dec 13 16:42:46 servername kernel: [    4.136853] sd 9:0:0:0: [sdf] Write Protect is off
Dec 13 16:42:46 servername kernel: [    4.137584] sd 9:0:0:0: [sdf] Mode Sense: 4f 00 00 00
Dec 13 16:42:46 servername kernel: [    4.138954] sd 9:0:0:0: [sdf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 13 16:42:46 servername kernel: [    4.231527]  sdf: sdf1
Dec 13 16:42:46 servername kernel: [    4.266020] sd 9:0:0:0: [sdf] Attached SCSI disk
Dec 13 17:12:51 servername kernel: [    4.089276] sd 9:0:0:0: [sdf] Very big device. Trying to use READ CAPACITY(16).
Dec 13 17:12:51 servername kernel: [    4.090840] sd 9:0:0:0: [sdf] 15628053167 512-byte logical blocks: (8.00 TB/7.28 TiB)
Dec 13 17:12:51 servername kernel: [    4.091678] sd 9:0:0:0: [sdf] 4096-byte physical blocks
Dec 13 17:12:51 servername kernel: [    4.092616] sd 9:0:0:0: [sdf] Write Protect is off
Dec 13 17:12:51 servername kernel: [    4.093612] sd 9:0:0:0: [sdf] Mode Sense: 4f 00 00 00
Dec 13 17:12:51 servername kernel: [    4.094610] sd 9:0:0:0: [sdf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 13 17:12:51 servername kernel: [    4.336744]  sdf: sdf1
Dec 13 17:12:51 servername kernel: [    4.362317] sd 9:0:0:0: [sdf] Attached SCSI disk
Dec 16 15:43:32 servername kernel: [253869.725465] sd 9:0:0:0: [sdf] tag#0 FAILED Result: hostbyte=DID_TIME_OUT driverbyte=DRIVER_OK
Dec 16 15:43:32 servername kernel: [253869.725474] sd 9:0:0:0: [sdf] tag#0 CDB: Read(16) 88 00 00 00 00 01 11 90 da 00 00 00 00 c8 00 00
Dec 16 15:43:32 servername kernel: [253869.725481] blk_update_request: I/O error, dev sdf, sector 4589672960 op 0x0:(READ) flags 0x80700 phys_seg 15 prio class 0
Dec 16 19:06:58 servername kernel: [    4.353200] sd 9:0:0:0: [sdf] Very big device. Trying to use READ CAPACITY(16).
Dec 16 19:06:58 servername kernel: [    4.354881] sd 9:0:0:0: [sdf] 15628053167 512-byte logical blocks: (8.00 TB/7.28 TiB)
Dec 16 19:06:58 servername kernel: [    4.374049] sd 9:0:0:0: [sdf] Write Protect is off
Dec 16 19:06:58 servername kernel: [    4.374733] sd 9:0:0:0: [sdf] Mode Sense: 4f 00 00 00
Dec 16 19:06:58 servername kernel: [    4.376145] sd 9:0:0:0: [sdf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 16 19:06:58 servername kernel: [    4.478754]  sdf: sdf1
Dec 16 19:06:58 servername kernel: [    4.521926] sd 9:0:0:0: [sdf] Attached SCSI disk
Dec 17 04:40:54 servername kernel: [    4.272884] sd 9:0:0:0: [sdf] Attached SCSI removable disk

```

The problem sdf is  a SD/MMC/MS PRO not a disk, see the lshw for device sdf

```

*-scsi:5
          physical id: e
          logical name: scsi9
          capabilities: emulated scsi-host
          configuration: driver=ums-realtek
        *-disk
             description: SCSI Disk
             product: SD/MMC/MS PRO
             vendor: Generic-
             physical id: 0.0.0
             bus info: scsi@9:0.0.0
             logical name: /dev/sdf
             version: 1.00
             serial: 2012062914345300
             capabilities: removable
             configuration: ansiversion=4 logicalsectorsize=512 sectorsize=512
           *-medium
                physical id: 0
                logical name: /dev/sdf

```

I disabled  uas ages ago with options usb-storage quirks=0bc2:ab38:u for each of the usb disks and all was working well.

Any idea what is going on ?


Kind Regards
Andrew

---

### Post by TheFu on 2021-12-17
How are your backups?  I've always found that if I have great backups, then when storage fails, it is a minor inconvenience, but if I didn't have any current backups, then it was a huge problem with at least a week of wasted time trying to figure out whether the disk was really dead (they always were) and worrying about all the data loss.

28% of the time disk failures show nothing clearly warning of the failure in the SMART data. Could be a cable, psu or controller problem.  Move the storage around and see if the issue follows those moves.

---

### Post by Andrew_Welham on 2021-12-18
backups are good, and i agree minor inconvenience, The weird bit is the error is reported on a device that is not there.

---

### Post by TheFu on 2021-12-18
> **Andrew_Welham said:**
> backups are good, and i agree minor inconvenience, The weird bit is the error is reported on a device that is not there.

A failing storage device lying to the OS doesn't seem all that weird to me.  If sdf isn't part of the RAID, why bring that up?  I see the brand - "Generic" ... is the whole system covered under warranty or should you just disable the MMC in the BIOS and ignore that storage going forward?

---

### Post by Andrew_Welham on 2021-12-19
The point is all that is the device sdf is not even used or part of a raid (which i'm not using), so i'm wondering if its some type of bug / setting

---

### Post by TheFu on 2021-12-19
> **Andrew_Welham said:**
> The point is all that is the device sdf is not even used or part of a raid (which i'm not using), so i'm wondering if its some type of bug / setting

It could be a bug, but more likely hardware failure sending bogus information.
> A failing storage device lying to the OS doesn't seem all that weird to me. If sdf isn't part of the RAID, why bring that up? I see the brand - "Generic" ... is the whole system covered under warranty or should you just disable the MMC in the BIOS and ignore that storage going forward? 

Looks like I brought up RAID. Don't know where they came from. I was helping someone else in these forums with some RAID issues, so I apologize for my confusion.

I'm back to the sdf device failing - or the controller connected to it.

Have you tried booting from a flash drive to see if a different Ubuntu sees that hardware differently?  If there has been corruption on the storage device where programs are located, those programs cannot be trusted. Using a Try Ubuntu USB flash boot device removes a number of issues. It is very handy to have one of those around to see if issues are tied to the other storage, other controller, installed programs, configuration, or user settings. Very handy indeed.

---

### Post by SeijiSensei on 2021-12-19
```

16 15:43:32 servername kernel: [253869.725465] sd 9:0:0:0: [sdf] tag#0 FAILED Result: hostbyte=DID_TIME_OUT driverbyte=DRIVER_OK
Dec 16 15:43:32 servername kernel: [253869.725474] sd 9:0:0:0: [sdf] tag#0 CDB: Read(16) 88 00 00 00 00 01 11 90 da 00 00 00 00 c8 00 00
Dec 16 15:43:32 servername kernel: [253869.725481] blk_update_request: I/O error, dev sdf, sector 4589672960 op 0x0:(READ) flags 0x80700 phys_seg 15 prio class 0
```
Errors like this usually mean the device is failing.

---

### Post by Andrew_Welham on 2021-12-21
I copied all the data  of a device sdE and the errors for sdF appear to have stopped as have the high iowaits. The device was slow to copy though. Did a mkfs on the device and its looks better.  The only part I  did not mention is all the devices are encrypted with LUKS , and have approx 16-20 K files added a day with 80K links made a day  with 5M+ files. I'm wondering if i have breached some limit or fragged  table some where. The i-nodes  were under 10% used.

The errors have gone and i can do some more work on the suspect  disk. Thanks for any ideas.

---

### Post by TheFu on 2021-12-21
I use LUKS. Never seen it add more than 3% overhead on systems with AES-SI support in the CPU.
I really hope you didn't to a mkfs on the entire device, but on a partition instead.  ALWAYS, ALWAYS, use partitions. Never put anything directly on a device except a partition table. This is really important for RAID setups, since many tools don't work if there isn't any partition table on a device.

5M files aren't that many, provided there are plenty of storage and inodes available.  I've run out of inodes on smaller allocated partitions before. What a pain.  The number of inodes pre-allocated is based on the size of the file system. For anything over 10G in size, the default allocation seems to be fine, but for smaller file systems, say a tiny web server full of static files or scripted webapps (ruby, python, perl) with lots and lots of module dependencies in the language, it is easily possible to run out.  

Let me see if I have that old system that ran out of inodes still .... 
```
$ df -Th
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/vda1      ext4      7.1G  [COLOR="#008000"]3.0G[/COLOR]  3.7G  45% /
/dev/vda2      ext4      2.3G  947M  1.2G  44% /var/www

$ df -Thi
Filesystem     Type     Inodes IUsed IFree IUse% Mounted on
/dev/vda1      ext4       454K  317K  137K   [COLOR="#FF0000"]70%[/COLOR] /
/dev/vda2      ext4       151K   58K   94K   39% /var/www
```

Yep. That's the one that ran out. My fix was to add a small partition just for web files even though less than 50% of the server storage was used.  I really should clean that system up by creating a new file system, but forcing 20x more inodes in the mkfs command. I really need to move that server to a fresh install, perhaps this summer after 22.04 is out and considered stable?

Anyway, I don't think anything related to inodes or LUKS involved here for issue in the thread.  I'd be more worried about SSD/Flash storage lifetime than anything else.

---

